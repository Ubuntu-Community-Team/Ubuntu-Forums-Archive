---
title: "Runing Ubuntu on a very old computer"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by jesusrop on 2005-07-24
I want to install Ubuntu in an old computer and use it mainly to print documents from any other computer in the network (obiously i will not buy a printer for each computer!). I've got some old hardware, and I'd like to know if I could run Ubuntu with a grafical desktop enviorement.

Here goes my hardware

Mobo: ASUS (unknown model)
Processor: Pentium II 350 MHz
RAM: 64 MB
Graphics: Asus AGP V3200
Sound: SB Live! value
HD: 4 GB (maybe also 40 more)
CD-ROM: 36x
Network: Unknown 10/100 Ethernet
Printer: HP deskjet 970 Cxi

I don't know if I forget something important.

Any idea of the result I will get?

Thanks again to everybody!

---

### Post by Xian on 2005-07-24
[Minimal Hardware Requirements](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch03s04.html)
[Supported Hardware](http://archive.ubuntulinux.org/ubuntu/dists/hoary/main/installer-i386/current/doc/manual/en/ch02s01.html)

---

### Post by Natja on 2005-07-24
Hum, ubuntu Lite is probably better for that computer.

see [http://www.ubuntulite.org](http://www.ubuntulite.org)

---

### Post by varunus on 2005-07-24
I would recommend using XFCE instead of GNOME for this type of computer.  There's a howto on how to install XFCE on Ubuntu without GNOME here:
[http://www.ubuntuforums.org/showthread.php?t=30896](http://www.ubuntuforums.org/showthread.php?t=30896)
(Xubuntu!  I said it.)

This will do a server install of Ubuntu (no graphical desktop) and then install a basic graphical desktop.  You'll need a good net connection, though, since you'll have to download XFCE and X-windows after installing.

XFCE is full featured, and works well with older (and newer, for that matter) hardware.

---

### Post by az on 2005-07-24
Everything being relative, I would suggest that you add more ram to the system.  64 megs of ram is not really enough for a gnome desktop system.  However, 128 megs of ram will leave you peasantly surprised at how well such an old system can perform.  It will deffinitely outperform WindowsXP with 128 megs of ram,

Some will reccommend lighter desktops, but if you do not have extremly high expectations, I would run the full-blown gnome (ubuntu-desktop) system on a 350 MHz machine and be happy with it.

---

### Post by czipeng on 2008-05-17
hi

what I want to know is that if ubuntu support the asua AGP v3200 display card?I bought a computer at 1999 and my monitor is philips 170s7

---

### Post by kerry_s on 2008-05-17
basically what you want is a remote printer server. for that you only need a server install and cups, no need to waste the already limited resources on a gui.
[http://www.ubuntu.com/products/whatisubuntu/serveredition](http://www.ubuntu.com/products/whatisubuntu/serveredition)

debian usually works better on the old stuff, just install the server stuff and skip the gui->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

---

