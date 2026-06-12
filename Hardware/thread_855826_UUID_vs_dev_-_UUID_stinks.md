---
title: "UUID vs /dev/*** - UUID stinks"
date: 2008-07-10
forum: Hardware
---

### Post by sofasurfer on 2008-07-10
Tried for days to get my hda hard drive to auto mount as a backup drive along with my sata boot drive. Was using UUIDs. I don't care what they say about the UUID method being better. It ain't better if it don't work. And it does NOT work.

No matter what, every time I boot the device names change and the UUID system can not compensate for it.

I just switched back to /dev/*** method and everything works fine.

---

### Post by sofasurfer on 2008-07-11
Woops!! I am wrong. I just got home and booted up. My 2 hard drives are named backwards and I can not access my backup hard drive.

This is rediculous. Can anyone help me solve this. And please don't tell me to use UUIDs. They make no differance. The problem is that the drives are named differant everytime I boot up. That is the problem. Why does this happen? You can't tell me that hard drives are supposed to have their names switched every time you boot up.

If anyone thinks they can troubleshoot this, please tell me what info you want and I will supply it. It is impossible to have automatic backups done with drives that are inaccessible.

---

### Post by picbits on 2008-07-11
I've had similar problems.

Set up 8.04 Server on an IDE 160Gb hard drive and added a 750Gb SATA drive as extra storage.

All was well until suddenly I couldn't access my recordings. Took me a while to work out that the drives had swapped their letters.

Just about to go through it all again - I've reinstalled the server, got mythtv up and running properly and need to get the extra storage online.

Will be interested to see if there are any resolutions to this problem.

---

### Post by sofasurfer on 2008-07-11
For right now it appears that I may have found the problem. My fstab entry for my boot drive contained a flaw as thus...

T/dev/sda1                          /                ext3         relatime,errors=remount-ro  0  1

Notice the 'T'.

I deleted this and so far so good.
I don't know if I accidently put that in there or if the system did it some how.

---

