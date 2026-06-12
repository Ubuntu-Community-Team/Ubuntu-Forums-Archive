---
title: "What scanner is my Mustek 1200CU, really? How do I fix it?"
date: 2009-08-10
forum: Hardware
---

### Post by duojet on 2009-08-10
Okay, I've been banging my head against the wall (well, not literally) trying to figure out a solution to this. I've read a ton of .man pages, and I'm ready to scream (yes, literally).

I'm using ubuntustudio 9.04 LTS

I have a scanner which is stamped with a Mustek BearPaw 1200CU logo.

lsusb shows this:

Bus 003 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6

sane-find-scanner returns this:

found USB scanner (vendor=0x05d8, product=0x4002, chip=GT-6801) at libusb:003:002

scanimage -L displays
device `gt68xx:libusb:003:002' is a Mustek ScanExpress 1200 UB Plus flatbed scanner

I've attempted to change permissions on several firmware files, and I've un and re commented the override in etc/sane/ for the 1200ub several times.

any ideas?

---

### Post by duojet on 2009-08-14
Ok, I'm an idiot. Before I purchased the 1200 CU at a thrift store, I was testing a scanner I got for someone else. That scanner was the 1200 UB plus. It has the same USB numbers. Something (not my .Sane folder) remembered it.

While trying to replace the much-hated VISTA on my other partition with XP, I ruined the partition table. One clean install of UStudio later, everything's fine. 

Plugged it in, downloaded firmware, works like a charm.

---

