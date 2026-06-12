---
title: "Intrepid - Intel X3100 - Glitchy 3D Graphics"
date: 2009-02-28
forum: Hardware
---

### Post by stang_318 on 2009-02-28
Hi.
I have a Compaq Presario C700 with an Intel X3100 graphics chip.
I recently installed Intrepid. Everything works great except for the 3D graphics, which is glitchy for some apps.

For instance, this is what Google Earth looks like when I try to use it:
[IMG]http://img4.imageshack.us/img4/4463/graphicsglitch.jpg[/IMG]

I can spin the planet, zoom in and out, and etc., but it never displays correctly.

The 3D rendering looks similar to the above for Tremulous and Atunnel screensaver.

However, most of the other 3D screensavers look fine. Glxgears works fine, too.

Here is the output for lspci:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)

```

Here is my xorg.conf (with comments edited out):
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Thanks

---

### Post by stang_318 on 2009-03-02
My issue is identical to the one submitted in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/262758]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/262758")

Disabling desktop effects solved nearly all of my rendering problems (this solution was not discussed in the bug report).
In
System-->Preferences-->Appearance-->Visual Effects
, there are 3 options:
     1)None
     2)Normal
     3)Extra (Compiz?)
All 3 settings work regarding desktop effects, but 3D rendering only works properly on the 'None' setting.

As I would like to use 'Normal' desktop effects, can I do something to help programmers fix this bug? (e.g. post my solution on the bug report) Better yet, does anyone know of any current ways of viewing desktop effects, together with correct 3D rendering, on an X3100 graphics chip?
I know jack about how the bug system works.

Thanks

---

### Post by crjackson on 2009-03-02
Not to mention how slow screen rendering is under Intrepid's xorg / intel drivers.

I went back to Hardy on my new laptop with the same video card, and it's much better than Intrepid.

---

### Post by stang_318 on 2009-03-03
I'm not experiencing performance loss in 3D rendering with Desktop Effects turned off. My fps in Tremulous is about the same for Ubuntu and Vista. I think performance drop is a different issue from rendering bugs.

---

