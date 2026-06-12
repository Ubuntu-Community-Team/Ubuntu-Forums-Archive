---
title: "ATI Radeon fan controll (11.04)"
date: 2011-05-27
forum: Hardware
---

### Post by Kubouch on 2011-05-27
Hello, here's my problem:

My computer often crashes, most probably because of my video card over-warming. I couldn't figure out how to change my fan speed. Linux ATI Catalyst (11.5) doesn't have the feature to change my fan speed. I tried to run ATI Catalyst in Wine but it says that I don't have 64-bit operating system (which is not true, my architecture and Ubuntu are both 64-bit). I also tried this page:

[http://forums.fedoraforum.org/showthread.php?p=1386622](http://forums.fedoraforum.org/showthread.php?p=1386622)

but it says:

No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configuration file manually and run aticonfig again.
aticonfig: parsing the command-line failed.

and when I try to run 'aticonfig --initial' I get:

Uninitialised file found, configuring.
Fail to link to fglrx-libglx.so, please check whether driver is installed correctly
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Permission denied.

I have my fglrx drivers installed successfully in System>Administrations>Additional drivers.

Here is my hardware & OS:

ATI Radeon HD4800 Series
Ubuntu Studio 11.04

Anyone can help please?

---

### Post by asd1618033 on 2011-05-27
hi 
I'm not using ubuntu anymore but I encountered in overheat problems with ubuntu and Ati 5470 in the past month.

xorg.conf is deprecated.

I'm using archlinux now and I resolved the overheat problem with creating
```
/etc/X11/xorg.conf.d/10-monitor.conf
```
Here you have to write down monitor/device/screen infos, like this example:
```
Section "Monitor"
    Identifier    "Monitor0"
EndSection

Section "Device"
    Identifier    "Device0"
    Driver        "fglrx" #Choose the driver used for this monitor
EndSection

Section "Screen"
    Identifier    "Screen0"  #Collapse Monitor and Device section to Screen section
    Device        "Device0"
    Monitor       "Monitor0"
    DefaultDepth  16 #Choose the depth (16||24)
    SubSection "Display"
        Depth     16
        Modes     "1024x768" #Choose the resolution
    EndSubSection
EndSection
```
Beware about resolution. I have 1366x736 (mine machine is a laptop) and 24 bit color depth.
In archlinux I had to disable KMS by adding nomodeset to kernel line in grub.
In this way the X server might load fglrx (ati proprietary drivers) and manage the GPU power (and heat, consequently).

---

### Post by Kubouch on 2011-05-28
Thanks, asd. It can be really helpful. However, I'd like to solve it without compete reinstallation of my OS :-).

---

### Post by asd1618033 on 2011-05-28
You don't have to re-install anything.
Simply edit (or create, if it doesn't exist) your 10-monitor.conf and paste the code above. 
Remember to edit video resolution.

---

### Post by Kubouch on 2011-07-02
[FONT=monospace]I have no such directory:

[/FONT]/etc/X11/xorg.conf.d/
And it's not possible to create any folder in /etc. Therefore I cannot put there 10-monitor.conf.

---

