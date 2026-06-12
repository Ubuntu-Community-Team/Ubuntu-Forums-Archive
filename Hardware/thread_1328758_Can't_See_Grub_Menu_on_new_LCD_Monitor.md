---
title: "Can't See Grub Menu on new LCD Monitor?"
date: 2009-11-16
forum: Hardware
---

### Post by Jose Catre-Vandis on 2009-11-16
Specs

Shuttle PC
Nvidia Geoforce 6200 Graphics card with DVI/VGA output
HannsG HH241 24" widescreen 1980x1080 WUXGA, HDMI 1.3 compatible
Multibooting @ 5 OS's

Connected up the HannsG using the supplied DVI-HDMI cable (HDMI connector on the monitor)

PC booted up fine with post screen viewable, then a blank screen for a few seconds (where grub menu usually is, then usual starting up for Xubuntu 9.04 (the default OS in my grub menu (grub legacy)

Once X was running everything fine.

Tried all sorts, reinstalling grub to mbr, reconfiguring X, checked for settings in bios (none obvious), but nothing changed.

So switched to VGA-VGA cable, and grub menu was back. So I am OK, but get a better picture and all round performance using the hdmi connection.

Previous monitor, an Iiyama 17" LCD worked fine on a DVI-DVI cable.

Any way to get the dvi-hdmi connection to give me a grub menu on boot?

Also, Xubuntu Progess screen during boot up is not centred, off to the right a bit, can I sort this by adding a vga=xxx to the bootline?

---

### Post by Jose Catre-Vandis on 2009-11-17
Think I have found a workaround - well its working so far.

Install grub2 on Jaunty or below
```
sudo apt-get install grub2
```

Test it by loading grub2 as chainloader (this option is offered on installation)
You'll need to "e" "e" and change root to uuid to get the chainloader to work

If you are happy run
```
sudo upgrade-from-grub-legacy
```
and grub2 will take over

And now it appears on boot up with DVI-HDMI cable :)

---

