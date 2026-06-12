---
title: "Dell Inspiron 5100"
date: 2010-01-31
forum: Hardware
---

### Post by kylilin on 2010-01-31
Hi guys!

Here's my scenario:

Got a Dell Inspiron 5100 with a busted hard drive, so I bought a replacement Western Digital Scorpio 160 GB. I installed it, booted the computer from an Ubuntu CD and installed it. Tried to boot fro, the hard disk and the computer couldn't recognize the hard disk. I upgraded the BIOS from A06 to A32 and tried again with no luck. 

Anyone have any pointers on what I may be doing wrong or what I can do to fix this?

Thanks in advance.

---

### Post by Yellow Pasque on 2010-01-31
Can you see the disk in the BIOS? If you can't, it could be a bad disk :/

---

### Post by kylilin on 2010-01-31
The disk shows up in bios. I've ran all the Dell diagnostics on it. right now, I have the computer booted up from a flash drive and I'm running diagnostics on the hard drive.

---

### Post by Yellow Pasque on 2010-01-31
Okay, so what happens when you try to boot?
> couldn't recognize the hard disk.
Is there a more specific error message? 
Does this help? [http://techie-buzz.com/ubuntu/restore-grub-ubuntu-9-10-karmic-koala.html](http://techie-buzz.com/ubuntu/restore-grub-ubuntu-9-10-karmic-koala.html)

---

### Post by kylilin on 2010-01-31
Sure, I get:

Hard disk read failure non bootable devices.

But I think the link you provided will work, I'll let you know.

---

### Post by kylilin on 2010-01-31
So I tried the following commands:

sudo fdisk -l

got the directory I wanted to boot from, which is /dev/sda1

then entered: sudo mount /dev/sda1/mnt

got this reply: mount: can't find /dev/sda1/mnt in etc/fstab or /etc/mtab

I am now banging my head against the wals.

---

### Post by Yellow Pasque on 2010-02-01
> sudo mount /dev/sda1/mnt
...
```
sudo mount /dev/sda1 /mnt
```

---

