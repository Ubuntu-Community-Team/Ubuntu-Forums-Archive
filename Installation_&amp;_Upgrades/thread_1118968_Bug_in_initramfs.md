---
title: "Bug in initramfs"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by cowboy.bebop on 2009-04-07
So I was trying to install buntu on my hdd, I have 3, I ended up getting the bug in iniramfs, SO I disabled all my other hdd's to find out which hdd was having the problem and my sata drive seems to be having the problem, is there anyway to fix this?

---

### Post by kellemes on 2009-04-07
> **Ubuntwha said:**
> So I was trying to install buntu on my hdd, I have 3, I ended up getting the bug in iniramfs, SO I disabled all my other hdd's to find out which hdd was having the problem and my sata drive seems to be having the problem, is there anyway to fix this?

What bug in initramfs do you mean?
So one of your drive's is kaput? Shouldn't this disk be replaced then?

To check a disk for errors.. (from a lifesystem)
```
sudo badblocks -s -v /dev/sda1
```
(Where sda1 is the disk you want to check)

---

### Post by cowboy.bebop on 2009-04-07
I do have windows have windows on the drive, but how would I run the sudo when it wont even boot to the live cd desktop, now this is what is wierd, I can boot into mandriva live np, but ubuntu wont let me, and I would prefer ubuntu of mandriva anyday.

---

