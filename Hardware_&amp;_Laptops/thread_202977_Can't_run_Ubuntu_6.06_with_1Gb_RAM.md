---
title: "Can't run Ubuntu 6.06 with 1Gb RAM"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by tangela on 2006-06-24
Hello, first I must say I don't speak english as well I want, but I'll try to explain what is my problem:
I've got a PC with a Gigabyte K8VT800 motherboard and a Athlon 64 3400+ sk 754.
I have also two RAM modules of 512 Mb each.
The Graphical Card is an ATI 9200 SE 128 mb ram
The system has two hard disk. The first is a Maxtor IDE 133 200 Gb on this  disk are installed two operating system: Microsoft Windows XP professional and Ubuntu 6.06 the second is a Maxtor SATA 160 GB which only has data, not applications.

When I run Windows all is right, but when I run Ubuntu (what I do very often) I must remove a RAM module because the system "hangs on" (doesn't work) when the graphical system starts (I can log in and see the mouse pointer and the wallpaper) and it does anything it doesn't answer neither the mouse or the keyboard. With 512 mb of RAM all is fine.

I have run memtest for 6 hours (16 pass) and the programs doesn't report any error.

Must I think about a motherboard slot fault? In other PC the RAM modules work well, but I can't try they on a motherboard like mine.

Can somebody help me? Thanks :???:

---

### Post by tukuyomi on 2006-06-24
Could it be a kernel limitation?
Have you tryied another arch-optimised linux kernel?
Depending on your processor, you can install a new kernel (K7 maybe, for AMD Athlon/Duron but don't know if it will suit your 64bit processor :/)...
```
sudo apt-get install linux-k7
```
Don't worry, your actual kernel will be kept, and if something goes wrong, you can select it through GRUB, before the boot process.

---

### Post by _simon_ on 2006-06-25
How strange!

Are you running 32bit or 64bit dapper?
What kernel are you running (from terminal enter uname -r)
Will the Desktop (live) CD/DVD load ok?
Is it a fresh install or an upgrade from a previous version?

---

### Post by tangela on 2006-06-25
Yes, it&#347; very strange.

I am running a 32 bit OS, kernel 2.6.15, and the live CD doesn't run. I want to try with the last Knoppix I will inform you.

Yesterday I was trying run with all the RAM and I boot the kernel in**_ recovery mode_**; from console I logged as root and type the command "startx". A warning message about **Power Manager** appears and says: "This program cannot start until you start the dbus system service". After I close it all the other programs (Firefox, Open Office, internet P2P...) seem to run well. :confused: 

This message appears also when I want to log out and sometimes I must press "Reset" button.
The System Monitor application recognizes 1011,8 Mib of RAM, and the BIOS 1.048 MiB RAM.

Has somebody any good idea? Thanks.

---

### Post by tangela on 2006-06-29
Can somebody say why I can run Linux with 1Gib RAM if the distribution is Mandriva (now) or Knoppix?
I installed mandriva One in my Hard Disk and it runs fine.

I like ubuntu, why I can't run it well????:(

---

### Post by hbweb500 on 2006-06-29
Well, for one, you said you were running a 32 bit version of Ubuntu on your 64 bit processor. If I were you, I would download the 64 bit version of Ubuntu here: [http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-amd64.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-amd64.iso) (or any other mirror, its the one labeled "64-bit PC (AMD64) desktop CD").

If that doesnt help, you may want to recompile your kernel with support for more RAM. But Mandriva works on your system, so I would say that the kernel is not your problem.

---

### Post by patrickfromspain on 2006-06-30
the kernel shouldn't be any problem... I've runned the i386 kernel with 1gig of ram with no problmes, also a friend had it running with 2gigs. 

I'd say it's some kind of hardware issue.. have to tried to put the ram module into another socket? If you now have sockets 1 and 2, change to 1 and 3 or 1 and 4 or whatever..

---

