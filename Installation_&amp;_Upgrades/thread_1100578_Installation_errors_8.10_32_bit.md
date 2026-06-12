---
title: "Installation errors 8.10 32 bit"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by gaoshearer on 2009-03-19
Good afternoon,

First off, Im a nubbie and hate being helpless, especially on such a huge forum. I have wanted to run Linux on two of my systems for awhile now and I have finally got the courage up to try it. I am having two errors on install of 8.10 32 bit. Im running this on a P4 1.8GHZ.

srst failed error when I try to install from CD boot
ata2: reset failed, giving up

I read another post that said about going in and changing the bios from IDE to RAID but I dont believe I have that option on this older system.

Please help.
Thank you

---

### Post by cariboo on 2009-03-19
The error your are getting indicates a hard drive problem. I would suggest making sure that all the connectors are seated properly and the jumpers are set correctly.

Jim

---

### Post by motrocco on 2009-04-28
I'm having this problem with a new install on a Mitac 8575

I am using it for linux but it has No cd-rom drive in it.  Yes it broke so I've installed using a network boot.

Yes it took ages to get it working (SIS900 netowrk card in it that doesn't like PXE), used Etherboot to load it up an modded the install script to load the boot install.

Yes I've spent all afternoon downloading packages etc. then when I reboot I get this error.

It is only loading in a RAMdisk as far as I can tell.

Not used linux in ages so I am rusty.  Anyone shed some light on this issue?  Checked the fs and I don't have /etc/modprobe.conf on the system.

Was my install screwed?

Please feel free anyone who has the SIS900 issue to get in contact.  It's quite simple to get around once you notice that it's the network card that's the problem.

Mot

---

