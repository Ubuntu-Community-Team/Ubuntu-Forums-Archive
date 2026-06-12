---
title: "nvidia_367 kernel module options ignored at boot, ubuntu 16.04, /etc/modprobe.d"
date: 2016-05-22
forum: Hardware
---

### Post by dmitry-a-durnev on 2016-05-22
Similar question was answered in 2012, but the solution not works in 2016. I used nvidia-graphics-drivers-367 to install nvidia beta 367.18 proprietary driver. I want to enable PCIe gen3 operation by using **NVreg_EnablePCIeGen3 **module parameter. Adding the line

```
options nvidia_367 NVreg_EnablePCIeGen3=1
```

to a separate file(named nvidia-gen3.conf) in /etc/modprobe.d directory usually worked(for previous driver versions). But sometimes (and in case of 367) the option seems to be ignored on boot. If I do the modprobe manually after boot(previously switching to VT console and removing nvidia modules), everything is OK: nvidia-settings reports PCI gen3 is enabled, *modprobe -v* adds module parameter on insert, but *systool -vm nvidia* still shows no parameters.(maybe module bug?) Wiith the same file present I get only PCIe gen2 after boot according to nvidia-settings at least. Is there some stable solution for this? Maybe some other module alias exists(tried nvidia and nvidia-current - no luck)? Or maybe there's some conflct with nvidia-graphics-drivers.conf in /etc/modprobe.d: for example module alias is added sometimes after my option? BTW adding kernel parameter nvidia.NVreg_EnablePCIeGen3=1 before boot seems to also not work...

---

### Post by normadize on 2017-02-26
After a few desk-head-bangs, the solution on my 16.04 is that I needed to also run update-initramfs in additional to adding a modprobe.d file.

Specifically, I installed the latest nvidia drivers from the ppa:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
[COLOR=#323333][FONT=Courier]sudo apt-get update
[/FONT][/COLOR]sudo apt-get install nvidia-378
```

Then created /etc/modprobe.d/nvidia-pcie-gen3.conf with the following contents:
```
# NOTE 1: you need to run update-initramfs after changing/adding this!
#         or else it won't get updated
# NOTE 2: You must use the actual driver name "nvidia_378" (or whatever
#         version you installed) and not the alias "nvidia"

options nvidia_378 NVreg_EnablePCIeGen3=1
```

Then run:
```
sudo update-initramfs
```

Then reboot.

---

