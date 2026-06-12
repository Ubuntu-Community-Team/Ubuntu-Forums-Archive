---
title: "mdadm RAID 5, not seeing 1 disk."
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by neoncode on 2007-07-25
I had a RAID 5 array over 4 identical 250GB hard drives, It was created using mdadm on Kubuntu 7.04 and I used it as my /home. However due to problems with my linux install, I decided to do a fresh install of Kubuntu. I figured it would be a good time to try out Gusty so I downloaded the Tribe 3 Kubuntu Altanate install CD (for x86) and installed it. I forgot to do the raid during the install so after installing the system I booted it and attempted to install mdadm. (My root partition is on a separate Hard Drive,)

After some reading of the man page I figured out how to assamble a pre-created array and ran the command:

```

sudo mdadm -A /dev/md0 /dev/sd[b,c,d,e]

```

However, this gave an error saying there was no superblock on /dev/sdb. I looked at /proc/mdstat and it listed an autodetected array called md127. I ran and mounted it and it was my array, I could view data on it from it's mount point and I thought that was it. However, /proc/mdstat did not list /dev/sdb as part of the array. At first I thought this was just the beta of kubuntu being buggy. So I decided to play it safe and downloaded a standard install disk for Kubuntu 7.04.

I booted into the Live CD and installed mdadm in there, before the actual installation. It autodetected md0 but again it only showed 3 of the devices as part of the array, /dev/sdb was again not there. I tried to assemble the array manually as before but this time instead of giving an error about a superblock on /dev/sdb it ran the array but gave an error

```
ubuntu@ubuntu:~$ sudo mdadm -A /dev/md0 /dev/sd[b,c,d,e]
mdadm: /dev/md0 has been started with 3 drives (out of 4).
```

However, if I mount /dev/md0 I can still access all my data, write to the array and it still shows the array as having the same amount of available space... but still mdstat does not show /dev/sdb as part of the array. I know that RAID 5 arrays can function missing 1 drive... so is mdadm simply not seeing sdb? Has it become corrupted somehow?

---

