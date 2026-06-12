---
title: "ATI Drivers."
date: 2005-10-09
forum: Hardware &amp; Laptops
---

### Post by Bengaul on 2005-10-09
Hi,

I have been following these [http://www.ubuntuforums.org/showthread.php?p=348911](http://www.ubuntuforums.org/showthread.php?p=348911) instructions for installing ATI Drivers onto breezy. I have been, as you can guess, unsuccessful. As mentioned in the thread I have the output of the commands that may lead to a solution.

I hope someone can help!

ben@Benubuntu:/home$ sudo fglrxinfo
Password:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

ben@Benubuntu:/home$ dmesg | grep fglrx
[4294715.822000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294715.828000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[4294715.828000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294715.830000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294715.830000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294715.830000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294715.830000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[4294715.831000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4294715.839000] [fglrx] free  AGP = 51113984
[4294715.839000] [fglrx] max   AGP = 51113984
[4294715.839000] [fglrx] free  LFB = 122679296
[4294715.839000] [fglrx] max   LFB = 122679296
[4294715.839000] [fglrx] free  Inv = 134217728
[4294715.839000] [fglrx] max   Inv = 134217728
[4294715.839000] [fglrx] total Inv = 134217728
[4294715.839000] [fglrx] total TIM = 0
[4294715.839000] [fglrx] total FB  = 0
[4294715.839000] [fglrx] total AGP = 16384
ben@Benubuntu:/home$ cat /etc/X11/xorg.conf | grep Driver
     Driver "kbd"
     Driver "mouse"
     Driver "fglrx"
ben@Benubuntu:/home$

---

### Post by mlomker on 2005-10-09
Are you using the drivers that came with Breezy or downloaded ones?

---

### Post by Bengaul on 2005-10-10
Hi, 

Thanks for replying, I used drivers that I downloaded from the ATI website.

---

### Post by mlomker on 2005-10-10
You should try reinstalling the .deb package, then.  It's supposed to overwrite the /usr/X11R6/lib/libGL.so.1.2 file, and that switches you from MESA:

```

dpkg -i --force-overwrite fglrx_6_8_0-8.16.20-1.i386.deb

```

---

### Post by Bengaul on 2005-10-10
Hi,

tried installing the .deb package, and no joy! Used sudo -s -H to run the package. Am a little out of ideas!

---

### Post by Bengaul on 2005-10-10
If it is any help, I get the ATI control panel under applications...

---

