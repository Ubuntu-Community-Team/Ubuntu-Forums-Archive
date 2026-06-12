---
title: "Unity with nVidia drivers on MacBook"
date: 2013-07-20
forum: Hardware
---

### Post by ZICODIAN on 2013-07-20
Sincerely, I am requesting assistance on this graphics problem. It has been ongoing for a long time now and I've tried to get assistance here a few times without much success.

[COLOR=#000000]I have a 2010 MacBook Pro 7, 1 ([/COLOR][http://www.everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.4-aluminum-13-mid-2010-unibody-specs.html](http://www.everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.4-aluminum-13-mid-2010-unibody-specs.html)[COLOR=#000000]) running 64 bit Ubuntu 13.04. Because of frequent crashes likely resulting from default graphics drivers, I installed the latest nVidia display driver ([/COLOR][http://www.nvidia.com/object/linux-display-amd64-319.32-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.32-driver.html)[COLOR=#000000]) and I am now unable to run Unity (or GNOME 3).

Specifically, after logging in via the standard login screen, the screen remains blank (with mouse pointer) and the graphics of Unity do not appear.

Do you have any ideas at all about how I could approach this problem? Any ideas at all, no matter how tentative, would be greatly appreciated. I just don't know what to do. Thanks.[/COLOR]

---

### Post by xEHYMRy on 2013-07-30
I have been having trouble with my nvidia gtx 675 M when I try to use their drivers as well.  At first I thought it was just the wrong driver, but it happened again with the latest release.  Mine will set the resolution to 640x480 with no other options.  I ended up removing xorg.conf file and rebooting to restore the default settings.

---

### Post by papibe on 2013-07-30
Hi ZICODIAN.

Could you post the results of these commands?
```
sudo lshw -C display

lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by ZICODIAN on 2013-09-15
Hi papibe. Thanks for your help on this. The outputs are as follows:

sudo lshw -C display
[COLOR=#000000]```
[/COLOR]
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:23 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:1000(size=128) memory:d3000000-d301ffff
[COLOR=#000000]
```[/COLOR]
lspci -nnk | grep -iA2 vga
[COLOR=#000000]```
[/COLOR]
04:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:08a0] (rev a2)
	Subsystem: Apple Inc. Device [106b:00c2]
	Kernel driver in use: nvidia
[COLOR=#000000]
```[/COLOR]

---

### Post by papibe on 2013-09-16
Thanks.

I recommend doing some cleaning and reinstall the driver from the repositories. If that does not work, I would upgrade the driver from the available ppa's (safer than the Nvidia driver from their site).

After you boot, press Ctrl+Alt+F1 to go to text mode. Login into your account and follow these steps:
[LIST]
[*]Get the list of Nvidia packages currently installed:```
dpkg -l  | grep nvidia
```
[*]Star purging the nvidia-* packages using this structure:```
sudo apt-get purge nvidia-304
```
[*]Remove all packages separately except for these two:```
nvidia-cg-toolkit
nvidia-common
```
[*]Then reconfigure nvidia common:```
sudo dpkg-reconfigure nvidia-common
```
[*] Remove the Xorg config file:
```
sudo rm -rf /etc/X11/xorg.conf
```
[*]At this point you can reboot and you should get your desktop back. You will be using the open source driver (nouveau).
[*]Now open a terminal and install the 'current' driver:
```
sudo apt-get install nvidia-current

sudo nvidia-xconfig
```
[*]Now restart your computer.
[*]If things still are not stable or the way you want, you may upgrade to the swat's ppa:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
sudo nvidia-xconfig
```
[*]Reboot again.
[*]Then if that doesn't work either, there's another ppa with bleeding-edge versions:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo nvidia-xconfig
```
[*]Restart again.
[/LIST]
I hope that helps, and tell us how it goes.
Regards.

---

