---
title: "How to mount a partition spaned over two drives - from ext HDD"
date: 2008-12-11
forum: Hardware
---

### Post by bakegoodz on 2008-12-11
I'm trying to help someone that had a external 1 TB Lacie drive die. I think it was just the encloser power supply. I hooked up the two 500 MB drives and analyzed them with fdisk and the "file" command. One of them has a partition table that is the size of both of them and the other it just is identified as data. I think it is a JBOD setup, or some simple method to span two drives as one.

Is there a command to mount both together? Another idea is that I also have a 1 TB drive I can copy both to the one drive, but I can't seem to google a method to do any of these tasks. I'm know my way around the command line and utilities like dd, but this has me stumped.

---

### Post by burguay on 2009-01-26
> **bakegoodz said:**
> I'm trying to help someone that had a external 1 TB Lacie drive die. I think it was just the encloser power supply. I hooked up the two 500 MB drives and analyzed them with fdisk and the "file" command. One of them has a partition table that is the size of both of them and the other it just is identified as data. I think it is a JBOD setup, or some simple method to span two drives as one.

Is there a command to mount both together? Another idea is that I also have a 1 TB drive I can copy both to the one drive, but I can't seem to google a method to do any of these tasks. I'm know my way around the command line and utilities like dd, but this has me stumped.

Hi!
Did you resolve this problem? I've got a similar Lacie drive broken too.
Tnx!

---

### Post by bakegoodz on 2009-10-27
The data wasn't important enough to spend anymore time on it. I did figure out how to merge two drives into one with dd, but it didn't work. I still would like to know how drives are spanned in external drives, I may see that issue again.

---

