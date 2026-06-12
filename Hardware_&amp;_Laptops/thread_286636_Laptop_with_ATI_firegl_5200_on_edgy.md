---
title: "Laptop with ATI firegl 5200 on edgy"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by PoZZyX on 2006-10-28
Hello,

I tried many procedures to install ATI graphics drivers on edgy, but I can't have 3d acceleration.

With :
```

$ sudo apt-get install xorg-driver-fglrx
$ sudo apt-get install linux-restricted-modules-$(uname -r)
$ sudo dpkg-reconfigure xserver-xorg

```
it worked on dapper (2200 fps on glxgears) but on edgy I've 150fps.

I tried this too :
```

sudo apt-get install xorg-driver-fglrx fglrx-control libqt3-mt
sudo aticonfig --initial

```
150fps too

With this 2 procedures I have the same result :
```
ccriniti@t60p:~$ glxgears -printfps
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
874 frames in 5.3 seconds = 165.455 FPS
```

```
ccriniti@t60p:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```

```
ccriniti@t60p:~$ dmesg | grep fglrx
[17179595.580000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179595.580000] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
[17179595.580000] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0

```

Can anyone help me ?

Thanks for you help ;)

---

