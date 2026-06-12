---
title: "Nvidia Geforce 840M driver. Black screen on boot. HP Envy 15"
date: 2015-03-19
forum: Hardware
---

### Post by johnmarka on 2015-03-19
This has been driving me nuts for way too long. I've tried everything I can find on the internet (including the helpful, and lengthy, discussion [here]("http://ubuntuforums.org/showthread.php?t=2262882")) and nothing wants to work.

It used to work fine until a couple of months ago, when for some reason my system booted to greet me with a blank screen. I was in a huge rush at the time so foolishly didn't check which updates had been done before this happened, I just uninstalled the nvidia drivers.

Basically whenever I install nvidia proprietary drivers, however I do it, I boot to a black screen where the login screen should be (the login sound still plays, suggesting it's just not being displayed on screen) from there I can CTRL+ALT+F1 into a terminal, uninstall the driver and then reboot.

My system has integrated intel graphics alongside the nvidia card.

Steps taken (that I can remember):
[LIST]
[*]Install drivers from Ubuntu repos (nvidia-331)
[*]Install drivers from ppa:xorg-edgers/ppa and ppa:mamarley/nvidia (both the suggested nvidia-340 version and the latest nvidia-346 version)
[*]Update xorg-config manually (according to advice on the internet)
[*]Update xorg-config with nvidia-xconf (having installed the drivers)
[*]Completely purge everything between installs (apt-get purge nvidia* / apt-get purge bbswitch-dkms / apt-get autoremove / apt-get autoclean / ppa-purge [ppa] / apt-add-repository -r [ppa] / rm /etc/apt/sources.list.d/[ppa]* / sudo apt-get autoclean)
[*]Updated the kernel twice (it was 3.13.0-46-generic, updated to 3.16.0.31-generic via apt-get install linux-generic-lts-utopic, then updated to 3.19.2-031902-generic via debs [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"))
[*]Tried booting with "nomodeset"
[/LIST]
The only thing that makes any visible difference was "nomodeset", which tends to (when nvidia drivers are installed) get me as far as the login screen, but then the system hangs during login before the desktop appears.

I'm now begging for some help. If anybody is kind enough to help me diagnose the problem properly. Thank you in advance.

I've now removed all traces of the nvidia drivers (as described above) and the xorg-edgers and mamarley ppas to have a clean start.

To get started:
```
$ sudo lshw -C display  *-display UNCLAIMED     
       description: 3D controller
       product: GM108M [GeForce 840M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b5000000-b5ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:5000(size=128)
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:31 memory:b7000000-b73fffff memory:c0000000-cfffffff ioport:7000(size=64)

```

System:
HP ENVY 15-j140na
Intel Core i5-4200M
Ubuntu 14.04 64bit

---

### Post by johnmarka on 2015-03-19
So, somehow I've made it worse... :(

I tried a few things, including installing via the script from nvidia's website and following the advice [here]("http://ubuntuforums.org/showthread.php?t=2263316") (which got me as far as the "freeze after login" problem mentioned above). Then I tried to revert back again (remove everything nvidia as described above), but now I seem to be in an even worse place. 

The standard ubuntu terminal window is just a big black square. Other windows (e.g. nautilus and xterm, but not chrome) have large black borders around them and missing window toolbars. The output of sudo lshw -C display still looks the same as above. What the hell has happened?

Edit: Removing xserver-xorg-video-intel will fix the problem with the window borders (I also removed the 3.19.2 kernel version, otherwise that would cause my mouse pointer to disappear) but drops me into some sort of low-graphics mode without transparencies etc.

---

### Post by johnmarka on 2015-03-20
The problem has now been fixed by a fresh install. Not an ideal solution, but it does work now.

For  completeness (and for the benefit of any poor souls who stumble across  this after days of trying to make their damn machine work) I'll put  exactly what I did here.

1. Backup. Download 14.04, make bootable  disk, install (manually, formatting the partition). Accept to install  updates and non-free stuff during installation
2. Boot up and enable the "partners" software sources via GUI
3. sudo apt-get update. sudo apt-get upgrade
4. Install proprietary wifi drivers via GUI (no nvidia drivers shown in "additional drivers" GUI)
5. Rebot
6. sudo add-apt repository ppa:xorg-edgers/ppa
7. ctrl + alt + f1 (takes you to a terminal screen, so make sure you've noted down the below if you're following along at home)
8.  sudo service lightdm stop (This stops the display manager. If you're  not using vanilla Ubuntu you may have to stop a different display  manager (like gdm or kdm or something))
9. sudo apt-get update
10.  ubuntu-drivers list (This lists the same proprietary drivers that would  be found in the "additional drivers" GUI. Since we've added the  xorg-edgers ppa this now includes an nvidia driver)
11. Note down the driver version suggested (mine was nvidia-340)
12.  sudo apt-get install nvidia-340 (which also installs a bunch of other  things, including bbswitch-dkms, nvidia-prime, nvidia-settings,  screen-resolution-extra...)
13. sudo poweroff
14. Boot up and login. All should be well at this point.
15. Open NVIDIA X Server Settings from the launcher to check it's all up and running.
16. ?????
17 PROFIT.

Nothing  particularly special there. Just installing the suggested driver from  xorg-edgers and exiting the UI and stopping the display manager before  installing just to be sure.

I've still no idea what got my machine so stuffed it needed a fresh install, but at least it now works.

---

