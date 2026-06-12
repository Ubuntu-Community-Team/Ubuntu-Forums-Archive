---
title: "cannot unmount external harddrive"
date: 2008-05-26
forum: Hardware
---

### Post by SCHWARTZMC on 2008-05-26
i am a noob running feisty on a dell inspiron 1420 laptop.

i have a Maxtor external harddrive formated in NTFS, which i am unable to unmount. every attempt gives me the error 'cannot unmount volume'

i haven't lost any data by simply unplugging it...yet

is there a way to properly unmount it?

---

### Post by nicedude on 2008-05-26
I have an external that does that and I have just powered it off like 50 times with no data loss ( and I have 400+ movies on that drive so I wouldn't be doing it if I wasn't pretty confident, although everything on it I have copies of elsewhere but it would be a pain to redo it ) I believe the way you might see data loss is if you had copied new data to the drive or modified data then just unplugged it before the write operation completed and sometimes the write operation is delayed by the system and normally when you select to unmount it will complete all pending operations before the unmount. In short I haven't had anything bad happen as a result of this but if anyone here knows more please chime in.

---

### Post by Positive on 2008-05-26
I presume noob means you don't know its mount point nor "name" like /sdbX

Open Terminal, type

mount -l

Find your external HD (if you have renamed it, you'll find it easier). 
In my case e.g. /dev/sdb1 on /media/EXTERNAL type fuseblk (rw,nosuid,nodev,noatime,blksize=4096) [EXTERNAL]

then 

sudo umount /dev/sdb1 (like in my case)

It will prompt you for your password and it should magicaly disappear from your desktop. good luk.

---

