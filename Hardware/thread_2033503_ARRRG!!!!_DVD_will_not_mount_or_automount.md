---
title: "ARRRG!!!! DVD will not mount or automount"
date: 2012-07-26
forum: Hardware
---

### Post by irish1967 on 2012-07-26
[LEFT]Has anyone solved this for 12.04. I have been digging and digging but still have found no answers!!! lshw shows the drive...but will not mount the D**N thing. [/LEFT]
 
Any help would be great.

---

### Post by thatguruguy on 2012-07-26
> **irish1967 said:**
> [LEFT]Has anyone solved this for 12.04. I have been digging and digging but still have found no answers!!! lshw shows the drive...but will not mount the D**N thing. [/LEFT]
 
Any help would be great.

A data DVD, or a video DVD?  If it's a video DVD, you have to follow [this guide]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/") to install the correct libraries.

---

### Post by irish1967 on 2012-07-26
it is a blank DVD.  I am trying to burn an ISO.  But I cant get the damn box to see the drive.

---

### Post by Grenage on 2012-07-26
I assume the drive can read discs, and the BIOS can boot from discs?  Basically, the drive definitely works ok?

---

### Post by irish1967 on 2012-07-26
Yep....if I go on the dual boot to win 7 it is fine.  Just not on Ubuntu 12.04 LTS
 
Just as a side note...the cd ejects after about 3 minutes...all by itself....after reboot.

---

### Post by Grenage on 2012-07-26
I know that this will sound slightly odd, but do you have an audio CD to hand, can you see if it will play it?

---

### Post by irish1967 on 2012-07-26
Spins but does not run.  It keeps spininng....but no joy on the cd playing

---

### Post by Grenage on 2012-07-26
Could you post your fstab?

```
cat /etc/fstab
```

---

### Post by irish1967 on 2012-07-26
I am going to rebuild.  I looked at my fstab and it looks totally junked out.  I am seeing UUID's rather than paths.  Also it is showing an error on the primary drive.  
 
Thanks for all the help.

---

### Post by thatguruguy on 2012-07-26
> **irish1967 said:**
> I am going to rebuild.  I looked at my fstab and it looks totally junked out.  I am seeing UUID's rather than paths.  Also it is showing an error on the primary drive.  
 
Thanks for all the help.

Actually, UUIDs are the preferred way of identifying drives in fstab now. But good luck, just the same.

---

