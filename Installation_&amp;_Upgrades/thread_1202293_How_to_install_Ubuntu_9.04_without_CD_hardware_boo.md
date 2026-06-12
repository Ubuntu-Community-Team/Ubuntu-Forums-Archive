---
title: "How to install Ubuntu 9.04 without CD hardware boot?"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by resander on 2009-07-02
A little bit of background first...

This is for a Fujitsu laptop (FMV Biblo NS70S) made for the Japanese market (a gift bought in Japan). The Japanese XP was replaced with English XP with SP2 and has been working fine for a couple of years until about a month ago when it was badly hurt by viruses. Data files could be read, but Internet and many other program functions only worked intermittently. The English XP had been installed with two partitions, drive c and d. I decided to dual-boot and installed Ubuntu on the 'drive-d' partition after having saved the Windows data files to memory sticks. I tried to fix the Windows virus problem by running the latest trial-version of Kaspersky anti-virus. This completely killed Windows XP that is now always hanging somewhere in itself during startup. It is useless of course so I want to reinstall Ubuntu-only on the laptop. At the moment a smallish Ubuntu is available via the dual-boot.

The first time I installed Ubuntu I managed to enter BIOS (don't remember how) and found there is no function for changing the boot media search order. On clicking spacebar possibly with Alt or Ctrl key (I think), a software 'emergency boot help' function sprang into life and that enabled me to install Ubuntu using the Live CD.

The problem is I don't seem to be able to repeat this procedure for the reinstall.   

When Live CD is in the drive Ubuntu can see the following:

Directories: Casper, Dists, Install, Isolinux, Pics, Pool, Preseed, ubuntu (with link)
Files: autorun.inf, md5sum.txt, readme.diskdefines.txt
Exe file:   wubi.exe         

Content of Install directory is:  mt86plus, readme.sbm, sbm.bin

Content of autorun.inf is:

[autorun]

open=wubi.exe --cdmenu

icon=wubi.exe,0

label=Install Ubuntu



[Content]

MusicFiles=false

PictureFiles=false

VideoFiles=false


With the files above visible to Ubuntu is it possible to reinstall without the hardware boot?

---

