---
title: "installation does not progress past squashfs error"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by sp0tz on 2009-05-16
I've downloaded several ubuntu-9.04 i386 (standard and alternate text only) disks and verified that they have the correct checksum, then burned them to several disks (using brasero now installing k3b). Every time I try to install ubuntu or try ubuntu via the install disk, the screen goes black and eventually returns entries like this:

[5963.125513]SQUASHFS ERROR: Sb_bread failed reading block 0x7b33d
[5963.125513]SQUASHFS ERROR: unable to read page, block 1ecc3eec size b85c
[5963.125513]SQUASHFS ERROR: zlib_inflate returned unexpected result 0xffffff

If I leave the computer on in this state (I went to the grocery store.), the computer produces several of these errors, and does not appear to progress past them. The machine has the following specs:

Intel Core2Duo Processor 2.4 Ghz.
4GB ram
320GB sata HD (with ubuntu64 installed)

it has ubuntu64 on it because I just upgraded the mobo/ram/cpu/gfx card. (... and the PSU.) The weird thing is that I can boot to the old OS just fine. (I'd still like a clean install, as ubuntu64 was hard to find software for and I think that the install gets 'dirty' after a couple of years. is that right? I mean, so many upgrades, etc...)


Anyways, If anyone can make sense of any of this, I'd much appreciate it. In the mean time, I'm off to try another install disk....

---

### Post by sp0tz on 2009-05-16
installed gnomebaker and burned with that, install worked beautifully. I plan on uninstalling brasero in the new installation.

---

