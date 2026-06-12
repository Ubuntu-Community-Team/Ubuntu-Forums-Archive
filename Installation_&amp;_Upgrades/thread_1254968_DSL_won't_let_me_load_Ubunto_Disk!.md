---
title: "DSL won't let me load Ubunto Disk!"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by CountZeroOR on 2009-08-31
So, I'm trying to install Ubuntu on my notebook old Compaq Latitude notebook computer. I'd tried previously, and found out the system didn't have enough memory for Ubuntu - so I'd tried installing Damn Small Linux instead. That would install, but I couldn't get it to work with my wireless card that I'd purchased (which would work under Ubuntu).

So, I bit the bullet, and ordered some more memory for my notebook, to get it up to a level that it would run Ubuntu. However, now the system won't load the Ubuntu disk at all. It doesn't even give me the Ubuntu splash screen. Help!

The notebook is a Compaq Presario 12XL401, and I've added 256 MB of memory to it.

---

### Post by presence1960 on 2009-08-31
make sure your CD/DVD drive is set to boot first in your BIOS.

---

### Post by CountZeroOR on 2009-08-31
> **presence1960 said:**
> make sure your CD/DVD drive is set to boot first in your BIOS.

It is - or at least it's booting before the hard drive. I can't set it to boot before the floppy drive. The Presario notebook's BIOS won't let me (it's a little odd).

I should mention that Grub is installed but the CD-ROM Drive isn't listed in Grub, and that I've forgotten my password for DSL. Oh, and there's an error message I've overlooked.

```
sr0: CDROM (ioctl) reports ILLEGAL REQUEST
```

EDIT: Okay, I've burned another disk, and this one's loading the splash screen. I'm trying this disk now.

---

### Post by CountZeroOR on 2009-08-31
Okay, now I'm getting a new error message. It's giving me the following messages

```
Buffer I/O Error on device sr0, logical block (a number)
end_request: I/O error, dev sr0, sector (another number)
```

Is it an issue with the new CD, is it an issue with my hard drive, or do I need to be trying some new commands?

EDIT: For the record, I am running the self-tests on the disk for defects on the disks, and if that passes I'm going to try to boot off the disk, but I wanted to make sure it wasn't a foregone conclusion first.

EDIT2: The test found errors in 11 files. Do I need to burn another install disk again?

---

### Post by CountZeroOR on 2009-09-01
Alright, I've burned install disk number 3. The disk passes a file check. I've run a memory test on the computer - that passes. Now, however, when I try to install, after the bar fills about 85%, the screen goes off. Not just black, but off. I'm also not getting any activity lights and I'm not getting any optical drive noise. I'm going try a straight boot off the CD and I'll let you know how that goes.

---

### Post by lisati on 2009-09-01
With 256Mb of RAM you might find that the "alternate" installation disk works better. 

I have managed to get Ubuntu working on a machine which only had 222Mb of available RAM - the performance wasn't great but it was usable if I didn't try to do too much at once.

---

### Post by CountZeroOR on 2009-09-01
> **lisati said:**
> With 256Mb of RAM you might find that the "alternate" installation disk works better. 

I have managed to get Ubuntu working on a machine which only had 222Mb of available RAM - the performance wasn't great but it was usable if I didn't try to do too much at once.

Hmm... it's not working for booting off the CD, so I may have to to try the Netbook distro then. Unfortunately, I don't know if the notbook I'm using (it's an older netbook - it shipped with ME) will boot off of USB.

---

