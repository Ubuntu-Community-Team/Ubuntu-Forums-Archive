---
title: "X on Tv via RGB"
date: 2006-05-16
forum: Hardware &amp; Laptops
---

### Post by basesoft on 2006-05-16
I have Radeon card. I connected the monitor to the DVI. I would like to connect the VGA output to the TV via RGB-SCART connector ([http://www.idiots.org.uk/vga_rgb_scart/]("http://www.idiots.org.uk/vga_rgb_scart/"))
I set up the PAL timing under the WINDOWS as an extended desktop with the PowerStrip. It is working perfectly with great picture quality. I would like to do it under the LINUX, but I don’t know the X configuration.
Could you please help me?

Thank you,
Tamas

---

### Post by segalion on 2007-09-12
I am trying same of you, and Im in trouble, I think because I have a laptop, and I allways have 2 displays...

First, you need to have the well-done cable:
[http://ryoandr.free.fr/english.html](http://ryoandr.free.fr/english.html) or [http://www.idiots.org.uk/vga_rgb_scart/](http://www.idiots.org.uk/vga_rgb_scart/)

and xorg config following isntructions in [http://www.mythtv.org/wiki/index.php/RGB_Scart](http://www.mythtv.org/wiki/index.php/RGB_Scart)

My problem is that I need this pseudo-TVOUT, and dualhead config.Thats mean: TV screen at TV resolution,  clone of LCD primary screen at higher resolution (and not in necesary same square relationship)

I have tried xinerama and mergedFB xorg.conf, but I have problems with this two:

With xinerama I have been able to get the TV with correct modeline and sync, but allways as a extension of the desktop (not clone). 

References  Xinerama: [http://www.ubuntuforums.org/showthread.php?p=1773624](http://www.ubuntuforums.org/showthread.php?p=1773624)

Anybody can help me to set xinerama and clone mode (with 2 diferent resolutions)?

With mergedFB seems that I can put screen resoution config: clone with 1024x768 in lcd and 720x540 in TV (virtualiced to 1024x768), but problem is that I cant put correct modeline (and sync) for TV. With mergedFB you can only set one screen and monitor config, and X sets the modeline 720 to primary monitor, not TV.

References MergedFB: [http://www.ubuntuforums.org/showthread.php?p=1773710](http://www.ubuntuforums.org/showthread.php?p=1773710)

Anybody can help me to set modeline to CRT2 in mergedFB?

Thanks in advance.

---

