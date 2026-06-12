---
title: "added second IDE hard drive, can't mount correct partition"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by Lemony on 2006-11-29
Hi,
I've just added a second IDE hard drive to my machine, it's a 250Gb western digital caviar, and have slaved it to my old drive, a 60gb maxtor diamondback, and am now trying to mount one of the partitions from that hard-drive into linux. The partition is a 211Gb vfat volume at /dev/hdb3.

When I add the drive to my fstab with the line:
```
/dev/hdb3	/home/sam/largedrive	vfat	defaults,umask=007 	0       1
```

I get the following message:
```
ALSA lib pcm_asym.c:101:(_snd_pcm_asym_open) Unknown field slave
```

and the drive appears to be mounted but I'm unable to access it even with a sudo command.

Any idea where I'm making my mistake?

Cheers,
Sam

---

### Post by Lemony on 2006-11-29
Fixed independently.

---

### Post by taurus on 2006-11-29
```
/dev/hdb3  /home/sam/largedrive  vfat  defaults,umask=000  0  0
```

---

