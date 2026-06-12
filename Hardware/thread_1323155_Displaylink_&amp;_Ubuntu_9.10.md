---
title: "Displaylink &amp; Ubuntu 9.10"
date: 2009-11-11
forum: Hardware
---

### Post by Delivereath on 2009-11-11
Hey everybody,

I'm trying since last week to use my displaylink monitor with Ubuntu. I first tried with 9.04 but wasn't able to get any good result. Then I switched to 8.10 and followed this : [http://mulchman.org/blog/?p=21](http://mulchman.org/blog/?p=21)

The display was working and after adding touchscreen driver everything runs fine. I tried the last Ubuntu release, 9.10. I was a bit surprise since the display driver seems to be included as the display turns on and becomes green (which was a step of the 8.10 procedure). I tried to edit the xorg.conf file in different ways but couldn't get anything better than a shell prompt. 

Does anyone know how to enable the display as the driver is already in the system ?

And by the way, what would be the best release for a 800*480 touchscreen display ? Ubuntu MID or Ubuntu Moblin ?

Thanks in advance !

---

### Post by ipauldev on 2009-11-17
I also get the green screen and am interested in how to activate the display driver if anyone knows. Also using Ubuntu 9.10.

Thanks in advance.

---

### Post by ipauldev on 2009-11-17
Looks like there's a lot of talk on the issue here:

[http://lists.freedesktop.org/archives/libdlo/](http://lists.freedesktop.org/archives/libdlo/)

---

### Post by rectagonal on 2009-12-03
Did anyone make any progress with this ?

I have made a few stabs at getting my own displaylink device running in 9.10 with no success getting 'X' to load. I can get the frame buffer driver to load , but I can't get 'X' to load onto it... frame buffer console takes it over everytime... In 9.04 I have been able to prevent this by blacklisting fbcon and it's dependencies but I can't blacklist fbcon in 9.10 for some reason. It keeps loading every time....

---

### Post by trubshac on 2009-12-04
I am having the same frustrations, as per my post at 
[http://ubuntuforums.org/showthread.php?t=1344039](http://ubuntuforums.org/showthread.php?t=1344039)

---

### Post by Crath on 2009-12-24
same problems here as well

---

### Post by pyro2927 on 2010-01-22
Hi guys,

I've recently switched over to Arch linux, but I had the same problem you are all describing with my Mimo-710s displaylink monitor.  I found the problem to be which order I was loading my displays.  I HAD to load X on the external displaylink monitor first, and sencond on my internal netbook display.

You obviously can't follow this guide, but the Xorg.conf at the bottom might help (I wrote the whole thing, so feel free to ask questions!)

[http://wiki.archlinux.org/index.php/DisplayLink]("http://wiki.archlinux.org/index.php/DisplayLink")

---

### Post by rockorequin on 2010-02-01
Re the fbcon problem, I had some partial success by disabling KMS with the nomodeset kernel option in Ubuntu 9.10 (ie to do this if using grub2, sudo gedit /etc/grub/default and add nomodeset after "quiet splash", then do an sudo update-grub and reboot).

Prior to this I was getting an error in the Xorg log saying that /dev/fb0 did not exist, and this seemed to be because fbcon had taken it over (because it did exist and was displaying output from fbcon).

With nomodeset, it seems to have helped in that I no longer get the "/dev/fb0 does not exist error", and I get different output on the screen (it says "usb 1-1: dlfb: set_par mode 1680x1050", which looks like the displaylink driver). 

Unfortunately Xorg log shows that it unloads the displaylink etc drivers just after loading dri. There's no indication as to why though. dmesg shows some activity from the DL driver:

[   12.309771] usb 1-1: dlfb: allocated 4 65024 byte urbs 
[   13.216143] usb 1-1: dlfb: set_par mode 1680x1050
[   13.265280] usb 1-1: dlfb: DisplayLink USB device /dev/fb0 attached. 1680x1050 resolution. Using 6890K framebuffer memory
[   13.266173] usbcore: registered new interface driver udlfb
[   13.266652] VMODES initialized
[   13.372206] usb 1-1: dlfb: open /dev/fb0 user=0 fb_info=e61d4800 count=1
[   13.374119] usb 1-1: dlfb: set_par mode 1680x1050
[   13.538686] Console: switching to colour frame buffer device 210x65
[   13.540542] usb 1-1: dlfb: set_par mode 1680x1050
[   13.921287] usb 1-1: dlfb: set_par mode 1680x1050
[   14.178923] usb 1-1: dlfb: open /dev/fb0 user=1 fb_info=e61d4800 count=2
[   14.178929] usb 1-1: dlfb: release /dev/fb0 user=1 count=1
[   17.311291] Linux agpgart interface v0.103
[   17.364655] [drm] Initialized drm 1.1.0 20060810

FWIW, I'm using the latest udlfb and xf86-video-displaylink drivers from git and the 2.6.32.7 kernel (I manually removed the udlfb driver that comes with it) and running a VM in VirtualBox.

---

### Post by ColombianGold on 2010-03-25
Hi,

Im having issues installing my adapter too. Everything is good until messing with xorg. The only way I got it working was in my winxp guest in virtualbox. Its not the best solution but at least it works.

Greetings

CG

---

