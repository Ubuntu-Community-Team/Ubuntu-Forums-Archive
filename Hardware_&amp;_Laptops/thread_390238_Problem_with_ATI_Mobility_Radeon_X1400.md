---
title: "Problem with ATI Mobility Radeon X1400"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by Conquersilent on 2007-03-21
Hello.
I've got a new Thinkpad T60 with an ATI Mobility Radeon X1400 128 Mb.
I installed the last version of Feisty fawn.

So I tried to install the official ATI driver from the ATI website ati.amd.com.
This one did not work....I couldn't even run the file. I setted the right to run it but it did not pop up a window when I clicked on this file, there just appeared another folder.....and....disappeared.

Then I tried to install the driver from the Ubuntu Repositorys.
This does not work too.

my xorg.conf file shows this:
> 
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"

if i type fglrxinfo i see this:

> matthias@matzemobil:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

I hope someone can help me because i tried nearly every how-to i found :(

---

### Post by Cesium on 2007-03-21
I have an ATI X1400 as well. This how-to worked for me:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

### Post by strabes on 2007-03-21
I have the exact same card. This guide worked for me: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The guide that cesium posted should work as well. It's always a good idea to have linux-restricted-modules installed

It's easier to download fglrx from the repos instead of the website.

---

### Post by elephant007 on 2007-03-21
I have the same card too and BOTH of the previously mentioned methods have worked for me, don't ask! HA HA

---

