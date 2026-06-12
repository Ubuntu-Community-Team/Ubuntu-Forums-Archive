---
title: "Windows 7 install"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by BigCityCat on 2009-01-28
I am about to install windows 7 beta. I am dual booting ubuntu and vista. I assume windows 7 will wipe out my grub boot loader. I have tried to use easy bcd in the past to install grub but unsuccessfully. Is there a way after the install that I can use the ubuntu install cd to re initiate grub instead of using easy bcd.

---

### Post by mgol on 2009-01-28
I don't know what is "easy bcd", but You can boot using LiveCD, mount the partition You have Ubuntu on, then execute:
```
sudo grub
> find /boot/grub/stage1
> root (hdX,Y)
> setup (hdZ)
> quit

```
Where X and Y will be shown by the "find" results (X is the disk number, Y is the partition number, counted from 0). Z is the disk number You want Ubuntu bootloader to install in. If You have just one disk, then X=Z=0.

If You have a separate partition for /boot, do "find /grub/stage1" instead of "find /boot/grub/stage1".

After a reboot GRUB should be back. You'll have to edit manually /boot/grub/menu.lst file, though, to gain access to just installed Windows 7 instance.

---

### Post by BigCityCat on 2009-01-28
perfect thanks.

---

### Post by BigCityCat on 2009-01-28
how would I edit menu.lst

I know how to bring it up, and I have a backup copy, but what exactly would I write to add windows 7 beta boot loader? I assume that it will probably use vista longhorn bootloader. This may be a better question for windows 7 forum.

---

### Post by mut80r on 2009-01-28
> **BigCityCat said:**
> how would I edit menu.lst

I know how to bring it up, and I have a backup copy, but what exactly would I write to add windows 7 beta boot loader? I assume that it will probably use vista longhorn bootloader. This may be a better question for windows 7 forum.

at the end (after end automagic list blahblah):

```

title Windows 7 Beta 1
root (hd0,x)
chainloader +1

```

where x is the partition windows 7 is on (counting from 0) so if it's on the 1st partition on your disk, x would be 0.

EDIT: Those are one's (1) in the code tag after title and chainloader, not L's

---

### Post by BigCityCat on 2009-01-28
Okay thanks. Looks like I am ready to give this a shot. In a couple days, lol I have to finish selling some stuff on e bay 1st. Can't risk the downtime. Thanks guys I will let ya know how it goes.

---

