---
title: "can't mount USB flash drive, didn't safely remove it first"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by felipe82 on 2008-01-21
Hi, I've been searching for a solution but I can seem to find anything that works.

I have a Kingston DataTraveler 1GB usb flash drive that worked just fine, but now I get a ¨mount: wrong fs type¨ error (see attachment). I'm sure this is because this morning I left my house in a hurry and just took the disk from my desktop PC (winXP) without doing ¨safely remove hardware¨.

I can access the drive with no problems in vista on the same laptop.

thanks a lot in advance

PD: sorry, but I haven't had time to read fstab manuals as I'm in the office right now and don't have much time, so any quick help would be appreciated.

---

### Post by jnylen on 2008-01-22
Try to fsck the drive (wait until that error message comes up, then do **sudo fsck /dev/sdb** ).  You will probably need to specify additional options to fsck.  If the initial check reports errors, run these commands:

**sudo fsck -a /dev/sdb** (this will automatically repair damages to your disk)
**sudo fsck -r /dev/sdb** (this will prompt you to repair damages and may fix some things the first command didn't)

I also try to run **sudo fsck -at /dev/sdb** on my usb drives every once in a while to scan them for bad sectors and mark the bad sectors as unusable.

If all else fails, copy the files to a folder on your Vista machine, format the drive using Vista, and try again.

---

