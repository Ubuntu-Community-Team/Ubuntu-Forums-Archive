---
title: "Freezes at ubuntu/gnome splash screen"
date: 2005-05-12
forum: Hardware &amp; Laptops
---

### Post by OneSeventeen on 2005-05-12
I am booting with the new live CD for my [HP Pavilion zv6005US](http://www.circuitcity.com/ccd/productDetail.do?oid=120278&com.broadvision.session.new=Yes&com.broadvision.session.new=Yes&BV_UseBVCookie=No&ct=0&BV_SessionID=@@@@0827353802.1114297791@@@@&BV_EngineID=ccccaddehejekfkcfngcfkmdffhdffo.0) (AMD 64/widescreen/wireless-g/ati) laptop.

After going through the config, gnome starts to boot up, and I Can move my mouse around and everything looks fine, but the splash screen that has the "Ubuntu: Linux for Human Beings" just sort of sticks there.

I've heard this can be a driver issue, since it is a pci express graphics card, but i don't know how to boot to the live CD and tell it to use something else.  (and I don't know what else to tell it to use).

Any tips?

---

### Post by Rik on 2005-05-12
At the text prompt, try booting with permutations of

linux  noapic nolapic acpi=off vga=771

depending on how well your hardware is supported, you may reach different stages in the boot process; I have noticed that things are a bit better with the later kernels (after an installation, not a live cd)

hope that helps

---

### Post by Tavis on 2005-05-13
I had the exact same problem with a Presario R4000, which I think is the same machine with a Compaq branding.  Gave up and installed Fedora (Core 4 Test 3), but Fedora won't detect the synaptics pad properly (probably due to lack of support in the kernel for /dev/psaux) and also won't detect the Radeon Xpress 200M (haven't located the problem yet) which means I'm stuck at 1024x768.  So I'd be eager to give up and reinstall Ubuntu if you get this worked out.  Keep us posted.

Cheers,
Tavis

---

### Post by Tavis on 2005-05-13
More specifically: The display driver is working fine, and is displaying at 1280x800 (unlike in Fedore).  Somehow, X correctly finds the synaptics touchpad an puts it in the configuration file, but the kernel driver does not seem to load.  /var/log/Xorg.0.log shows that X cannot find the device, and indeed a listing of /proc/bus/input/devices does not show the device present.  (My external USB mouse works fine).  I just upgraded to kernel 2.6.11, same behavior.

It freezes either right after I log in, or, if I try to change the session, as soon as I click on the radio button to select a different session.  It's actually the whole machine that freezes, not just X (i.e., I lose my ssh connection).  I've tried turning off ACPI, and setting pci=routeirq, to no avail.  No funny log messages that I can find.

Probably the next thing to do is see if there are any synaptics/alps patches that aren't in the Ubuntu 2.6.11 kernel....


Cheers,
Tavis

---

### Post by Tavis on 2005-05-13
Here I go following myself up again.... the lockup definitely has something to do with the graphics driver, because when I reconfigure X to use the generic VGA driver, it does not lock up.  However, the generic VGA driver on this machine seems only to be capable of displaying 320x200, which is not exactly a usable configuration....

---

### Post by OneSeventeen on 2005-05-27
I just wanted to check up on this in case someone has found a good driver for the ATI Radeon Xpress 200M so this doesn't happen.

I'm a newbie to linux (have a few servers, but doing server stuff on generic PCs is easy compared to workstation/laptop stuff), so be warned I'll probably ask questions if I can't figure it out via google.

I'd really like this to work, over at linuxquestions it seems nobody has found a distro that works with this model of laptop :(

---

### Post by NickB on 2005-05-30
See my posts here [http://ubuntuforums.org/showthread.php?t=36991](http://ubuntuforums.org/showthread.php?t=36991)

Nick

---

### Post by snake1984 on 2005-08-03
[QUOTE=Tavis]I had the exact same problem with a Presario R4000, which I think is the same machine with a Compaq branding.  Gave up and installed Fedora (Core 4 Test 3), but Fedora won't detect the synaptics pad properly (probably due to lack of support in the kernel for /dev/psaux) and also won't detect the Radeon Xpress 200M (haven't located the problem yet) which means I'm stuck at 1024x768.  So I'd be eager to give up and reinstall Ubuntu if you get this worked out.  Keep us posted.

Cheers,
Tavis[/QUOTE]

The proprietary driver's on ATI's website now supports the X_00 PCI-E cards.

---

