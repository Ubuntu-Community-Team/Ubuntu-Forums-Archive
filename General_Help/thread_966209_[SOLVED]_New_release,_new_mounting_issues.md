---
title: "[SOLVED] New release, new mounting issues"
date: 2008-11-01
forum: General Help
---

### Post by gb5757870 on 2008-11-01
I'm really disappointed that despite all the hype surrounding this new release that mounting of local hard drives continues to be such a pain. 

I have a really simple set up:
Win XP OS partition - fat32
Data partition -      fat32

I know that a lot of developers have spent a lot of time developing this release like all others but how is it possible that with each release, I have to spend hours getting the shared "Data" partition (dual-boot with Windows) getting mounted automatically. And based on posts, I'm not the only one either.

After the usual trawling through forums, I finally got it working.
This fat32 partition is at /dev/sda4 and this is what I have in my fstab:

/dev/sda4                                  /media/sda4    vfat         utf8,umask=007,gid=1000     0  1  

The drive mounts with no problems but during the boot up I get an error saying to the effect "special device /dev/disk/by-uuid/28F8-BB71 does not exist."

The drive actually mounts ok but if it is, why am I getting this error?

Is it just me?

---

### Post by unclejac on 2008-11-01
If you look at your FSTAB does the UUID 28F8-BB71 correspond to your CD/DVD drive ?

---

### Post by gb5757870 on 2008-11-01
Thanks for the reply. Through some act of divine intervention, message no longer coming up and can still write to that partition. Closing this thread, hopefully never to rear it's ugly head again!

---

