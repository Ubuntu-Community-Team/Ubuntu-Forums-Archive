---
title: "GUI won't load / garbled display"
date: 2010-10-25
forum: Hardware
---

### Post by bdr909 on 2010-10-25
When I try to boot the Ubuntu live CD, the screen goes completely garbled before the GUI loads. I was thinking it may be video card related; I've got an GeForce 7800 GT, for what that's worth. I've tried both 32- and 64-bit versions.

Also FWIW, I am able to get the GUI to load with Mint's compatibility mode, but don't see an equivalent option in Ubuntu.

Any ideas or input?

---

### Post by pete25r on 2010-12-27
I've got the same issue.

Trying to boot 10.10 DVD, USB Stick or USB Drive, I get the normal boot screen, the VMLINUX part, a little more test and then the human/keyboard image. Next image I see on the screen is black and garbled bars up and down. No cursor no nothing.

Hardware, Giga Byte MA770(I think, its an AMD board), geforce 7800

there might be a bug report or something, I'll check and post it here if I find anything.

---

### Post by amsterdamharu on 2010-12-27
Mint has a kernel parameter called xforcevesa the initrd will (if this parameter is provided) create an xorg.conf telling xorg to use vesa drivers (low resolution but works on most cards).

I think Ubuntu defaults to nouveau drivers that should work with nvidia cards as well.

Since the live session runs out of memory you can't use installing and reconfiguring to solve it because after a reboot everything is gone. It looks like kernel parameters might be the best option here.

When you boot and get the menu with "try ubuntu" it should give you an option to edit the menu item as well. When you edit the entry there should be a line saying:
```
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper ...
```
change that to
```
append initrd=/casper/initrd.lz boot=casper  nouveau.modeset=0 rdblacklist=nouveau blacklist=vga16fb nouveau.noaccel=1 xforcevesa --
```

Then boot and see if it at least gives you an option to see something. 

Pressing control + alt + F1 after the CD is done booting and the screen is garbled. It should give you a text only login screen. 
From there I might direct you to install the needed driver and check if it works without a reboot. Just make sure you have the nouveau out of there because if that's loaded you need a reboot after installing the driver and as stated before you can't do that with a live session. ([unless you have way too much time]("http://ubuntuforums.org/showthread.php?t=1642953"))

---

### Post by pete25r on 2010-12-27
found a bug.. looks like AmsterdamHaru hit the nail on the head. Geforce 7800 and some later models have issues....

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/219751](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/219751)


AmsterdamHaru, I'm going to give your fix a go. Thanks for your input.

---

### Post by pete25r on 2010-12-27
ok, slight problem. It goes haywire just before, I believe, the boot options come up. As in I get no "try, install..." no options. Boots to text as normal, human/keyboard thing, Ubuntu logo with the balls under it, they change color for a little while, looks normal, and then black screen for a moment then it ends in garbled display. 

Is there a way to boot a USB Ubuntu drive, on another laptop/desktop, install the drivers and then boot up successful on the machine with the geforce 7800?

I'll post the lspci here once I get it up, if it'll help anyone.

---

### Post by amsterdamharu on 2010-12-27
You're booting off usb so you can edit the syslinux.cfg. Can you try adding the nosplash option to the syslinux.cfg?

I created a bootable iso using unetbootin (is in the Ubuntu repositories and is available for Windows). It will create the syslinux.cfg in the root of the usb disk.

If you post it I can edit it for you to what works for me on Mint.

I will be off soon but back in about 5 hours.

---

### Post by pete25r on 2010-12-28
ok did the put the drivers on the usb stick thing. didn't work. came up with some error saying no default boot options. 

researching the nosplash option...

---

### Post by pete25r on 2010-12-28
here's what the syslinux.cfg says

include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo

couldn't find a sample one to cheat off of...

---

### Post by amsterdamharu on 2010-12-28
Try mine, I removed the seed file but that don't matter:

```
default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/casper/initrd.lz boot=casper  nouveau.modeset=0  rdblacklist=nouveau blacklist=vga16fb nouveau.noaccel=1 nosplash  xforcevesa --

label ubnentry0
menu label Start Linux Mint
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper  nouveau.modeset=0 rdblacklist=nouveau blacklist=vga16fb nouveau.noaccel=1 nosplash xforcevesa --
```

---

### Post by pete25r on 2010-12-28
got bored.. downloaded Mint 10, made a USB boot drive and a boot cd.. they work on the desktop in compatability mode.

I adjusted the Ubuntu USB stick with the syslinux.cfg stuff above. Test run time!

---

### Post by pete25r on 2010-12-28
it works!

the UNetbootin thing had two options: default and Start Linux Mint

I just copy/pasted cause everything looked good to me. I'll go and type it up to say Ubuntu or something silly.

Thanks for your time amsterdamharu. Dank u wel.

---

### Post by amsterdamharu on 2010-12-29
Graag gedaan.

---

