---
title: "problem trying to install bumblebee"
date: 2015-10-06
forum: Hardware
---

### Post by Bisneff on 2015-10-06
Hi everyone

I'm on Ubuntu 14.04, running on Asus n550jv. 

I just tried to install Bumblebee following [this link]("http://linux-on-n550.blogspot.it/p/n550jv-issues-and-fixes.html") step 3

After rebooting I get black screen. So I run

```
sudo apt-get purge --auto-remove bumblebee-nvidia
```

reboot again just to see my pc freezing on "UBUNTU" startup message. 
so reboot in recovery mode and execute

```
sudo apt-get install nvidia-331 nvidia-331-update

```

reboot again. now I have log in screen but cannot login, so I hit ctrl+alt+f1, log from terminal and run

```
sudo apt-get purge nvidia-*
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

```

it made the trick and now I'm writing from my ubuntu 14.04

what's the matter? I've got feeling I've messed up a lil bit, so run

```
lshw -c video
```

giving this output:




>   *-display               
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: latency=0
       resources: irq:51 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)



as you can se "configuration:" is empty and the Nvidia card (previously with noveau driver) is simply disappered.

I've tried:
```

sudo apt-get install nouveau-firmware
sudo dpkg-reconfigure xserver-xorg

```

it makes the "configuration: driver=i915" entry appear, but still no nvidia.

Any suggestions?

---

### Post by Bisneff on 2015-10-06
update 

/etc/X11/xorg.conf doesn't exist in my pc. instead there is a xorg.conf.10062015 witch looks like a backup I made ...

here cat:

> Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection




EDIT:

Looking this:

> $ grep Driver /etc/X11/xorg.conf.10062015 
    Driver "intel"
    Driver "nvidia"
$ grep LoadModule /var/log/Xorg.0.log
[    31.025] (II) LoadModule: "glx"
[    31.427] (II) LoadModule: "intel"
[    31.555] (II) LoadModule: "dri2"
[    32.368] (II) LoadModule: "evdev"
[    32.463] (II) LoadModule: "synaptics"


I know I'm using the intel module for graphic...but how I can get back nvidia and use it?

---

### Post by efflandt on 2015-10-06
Since you purged nvidia* you currently have no nvidia driver and I am not even sure how to try the default nouveau driver for nvidia graphics on a laptop with hybrid Intel/Nvidia graphics. You could either try installing **nvidia-331-updates** package which has been working for my GTX 765M (and is now a newer nvidia driver version) or since nvidia.com suggests a 352 driver for you GT 750M (if that is what you have) you might try the suggestion I made in [http://ubuntuforums.org/showthread.php?t=2297785&p=13368943#post13368943](http://ubuntuforums.org/showthread.php?t=2297785&p=13368943#post13368943) about installing **nvidia-352** from graphics-drivers/ppa.

Although, I guess I should go try that on my laptop (which is currently still using nvidia-331-updates).

---

### Post by Bisneff on 2015-10-07
Thank You for your answer.

May I ask something to do if nvidia-352 end in black screen as bumbleebee and nvidia-331 ?

---

### Post by dino99 on 2015-10-07
Avoid old howto/wiki, and broken / unmaintained packages. Looks like you should activate xorg-edgers ppa to get nvidia-355 (and then deactivate it after driver installation.)
[http://ubuntuforums.org/showthread.php?t=2297755&p=13369030#post13369030](http://ubuntuforums.org/showthread.php?t=2297755&p=13369030#post13369030)

---

### Post by Bisneff on 2015-10-07
> **dino99 said:**
> Avoid old howto/wiki, and broken / unmaintained packages. Looks like you should activate xorg-edgers ppa to get nvidia-355 (and then deactivate it after driver installation.)
[http://ubuntuforums.org/showthread.php?t=2297755&p=13369030#post13369030](http://ubuntuforums.org/showthread.php?t=2297755&p=13369030#post13369030)

Thanks

so, moving through this thread-inception I didn't get what I can do. My bad, but probably I'm too newbie to get the point. 

A quick recup? 

Only thing I (maybe) understand is that nvidia driver will give me black screen problem and I'll need some workaround to avoid.

---

