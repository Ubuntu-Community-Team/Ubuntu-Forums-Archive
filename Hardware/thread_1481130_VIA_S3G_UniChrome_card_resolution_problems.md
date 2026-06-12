---
title: "VIA S3G UniChrome card resolution problems"
date: 2010-05-12
forum: Hardware
---

### Post by thanasis57 on 2010-05-12
After some help I managed to partially solve the resolution problems that haunt this type of card, so I just post the solution.

My screen is 1280x800, a resolution not supported neither by the vesa, proprietary unichrome, or openchrome drivers (I tried all of them on various Ubuntu distros).
** Vesa** only allowed 800x600 and 640x480.
** Unichrome** was only available until ubuntu 7.10 and still didn't work well.
** Openchrome** gave a beautiful 1280x800 resolution, but hang almost immediately and the laptop required a hard boot.

On the 10.04 distro, I managed to get a 1024x768 resolution after tweaking the following files:

**/etc/modprobe.d/blacklist-framebuffer.conf**
comment out:
"blacklist vesafb"

**/etc/default/grub**
delete: "quiet" and "splash"
add: "vga=0x318"
then,  to update grub
```
sudo update-grub2
```


**/etc/modules**
add lines:
fbcon
vesafb

**/etc/X11/xorg.conf**
First generate an xorg.conf file. Open terminal with Ctrl+Alt+F1 and run:
```
Xorg -configure
```Then edit the file and define the driver as fbdev:
Driver "fbdev"

This will force the framebuffer to use a 1024x768 resolution. It is not very beautiful, but it allows one to work.

One thing is for sure. I'm never buying a VIA chipset EVER again!

PS: System info
```
$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)

```

---

### Post by dino99 on 2010-05-12
maybe some help here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/197514](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/197514)

look how the xorg.conf is made (oldish config, but )

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=270667](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=270667)

---

