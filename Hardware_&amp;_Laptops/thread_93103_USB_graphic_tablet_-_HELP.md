---
title: "USB graphic tablet - HELP"
date: 2005-11-21
forum: Hardware &amp; Laptops
---

### Post by asipi on 2005-11-21
Hi,

I have a Conceptronic USB graphic tablet and I am not able to use it under Breezy. Some kinds of other distros can handle, so I hope Breezy will could also. (I like Ubuntu, and do not want other :) )

dmesg says this:
```
[4318876.281000] hiddev96: USB HID v1.10 Device [ACECAD USB Graphics Tablet ] on usb-0000:00:07.2-1
[4318876.282000] usbcore: registered new driver usbhid
[4318876.282000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver

```

so this should be an acecad type, and as I remember, so it was in another distro.

But:
I am not so expirienced to make the kernel and X modules from source downloaded from [http://acecad.sourceforge.net](http://acecad.sourceforge.net) :( I completely do not understand the README... (ok the config section is not a problem)

If anyone could help would be appreciated...

---

### Post by Dragonbite on 2006-01-24
I was lucky, I got my tablet before I installed Breezy, so I made sure it was plugged in during installation.  Before that, though, I had it plugged in when I booted up to an Ubuntu LiveCD it was recognized and usable which gave me hope for the installation to work.

It detected it and now it works, though I haven't been able to check the pressure sensitivity yet.  Mine is an Adesso Cybertablet.

If you can't find much for your tablet, look under Wacom and see if any of what they suggest for that one works for yours.

Here are some links I've come across
[Wacom Tablet-HOWTO]("http://www.tldp.org/HOWTO/Wacom-Tablet-HOWTO.html")
[An Ubuntu Forum Posting]("http://www.ubuntuforums.org/showthread.php?t=27520&highlight=graphic+tablet")
and
[Linux Wacom Project]("http://linuxwacom.sourceforge.net/")

Good luck, post what you find out because like I said I haven't tried it much yet so I don't know how well it works.

---

