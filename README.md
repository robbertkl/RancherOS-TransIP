# RancherOS on TransIP VPS

This repo contains instructions to install [RancherOS](http://rancher.com/rancher-os/) on [TransIP VPS](https://www.transip.nl).

## Installation steps

* Order a new VPS
* Install the VPS with any Linux distro (will determine the icon for the VPS, has to be a Linux distro)
* Go to the console
* Right after the VPS starts booting, it will say "Press CTRL-B for the iPXE command line"; do this quickly
* You might have to restart the VPS a couple of times to get it at the right time
* On the `iPXE>` prompt, run:

```
dhcp
set base-url http://releases.rancher.com/os/latest
kernel ${base-url}/vmlinuz rancher.password=rancher
initrd ${base-url}/initrd
boot
```

* Wait for the VPS to boot RancherOS
* After booting, ssh to the machine (user *rancher*, password *rancher*):

```
ssh rancher@<ip>
```

* Create/fetch/scp your `cloud-config.yml` (make sure it contains your SSH keys)
* Run the installer:

```
sudo ros install -c cloud-config.yml -d /dev/vda
```

## Authors

* Robbert Klarenbeek, <robbertkl@renbeek.nl>

## License

This repo is published under the [MIT License](http://www.opensource.org/licenses/mit-license.php).
