---
title: "Problem to install nvidia driver."
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by nadavvin on 2006-11-24
Hello

I just install ubuntu edgy and I try to set my nvidia card GEFORSE2 with:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html)

```

$ glxinfo | grep rendering
direct rendering: No
nadav@nadav-desktop:~$ sudo apt-get install nvidia-glx-legacy nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-legacy-kernel-source
Recommended packages:
  nvidia-glx
&#1492;&#1495;&#1489;&#1497;&#1500;&#1493;&#1514; &#1492;&#1495;&#1491;&#1513;&#1493;&#1514; &#1492;&#1489;&#1488;&#1493;&#1514; &#1492;&#1493;&#1500;&#1499;&#1493;&#1514; &#1500;&#1492;&#1497;&#1493;&#1514; &#1502;&#1493;&#1514;&#1511;&#1504;&#1493;&#1514;:
  nvidia-glx-legacy nvidia-settings
0 &#1502;&#1513;&#1493;&#1491;&#1512;&#1490;&#1497;&#1501;, 2 &#1502;&#1493;&#1514;&#1511;&#1504;&#1497;&#1501; &#1495;&#1491;&#1513;&#1497;&#1501;, 0 &#1497;&#1493;&#1505;&#1512;&#1493; &#1493;-0 &#1500;&#1488; &#1497;&#1513;&#1493;&#1491;&#1512;&#1490;&#1493;.
&#1510;&#1512;&#1497;&#1498; &#1500;&#1511;&#1489;&#1500; 3574kB &#1502;&#1514;&#1493;&#1498; &#1492;&#1488;&#1512;&#1499;&#1497;&#1493;&#1504;&#1497;&#1501;.
&#1488;&#1495;&#1512;&#1497; &#1508;&#1512;&#1497;&#1505;&#1492; 11.1MB &#1504;&#1493;&#1505;&#1508;&#1497;&#1501; &#1497;&#1492;&#1497;&#1493; &#1489;&#1513;&#1497;&#1502;&#1493;&#1513;.
Get:1 http://security.ubuntu.com edgy-security/multiverse nvidia-glx-legacy 1.0.7184+2.6.17.6-1 [3070kB]
Get:2 http://il.archive.ubuntu.com edgy/restricted nvidia-settings 1.0-3ubuntu7 [504kB]
Fetched 3574kB in 55s (64.1kB/s)                                               
Selecting previously deselected package nvidia-glx-legacy.
(Reading database ... 99138 files and directories currently installed.)
Unpacking nvidia-glx-legacy (from .../nvidia-glx-legacy_1.0.7184+2.6.17.6-1_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_1.0-3ubuntu7_i386.deb) ...
Setting up nvidia-glx-legacy (1.0.7184+2.6.17.6-1) ...

Setting up nvidia-settings (1.0-3ubuntu7) ...

nadav@nadav-desktop:~$ sudo nvidia-glx-config enable 
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.


```

---

### Post by Majiman on 2006-11-26
It appears that they changed the way you enable the nvidia driver and didn't change the comments in the package.  Use:

sudo nvidia-xconfig

I had the same problem too until I found this thread:  [http://www.ubuntuforums.org/showthread.php?p=1776715](http://www.ubuntuforums.org/showthread.php?p=1776715)

---

