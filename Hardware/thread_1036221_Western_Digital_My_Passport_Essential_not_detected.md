---
title: "Western Digital My Passport Essential not detected on Intrepid"
date: 2009-01-10
forum: Hardware
---

### Post by beefysam128 on 2009-01-10
So here's the story, I recently purchased a 250gb WD My Passport Essential for my desktop as a backup drive. The problem is when I plugged in the hard drive in my computer Ubuntu Intrepid did not detect the drive. Any drivers needed? 

Thanks!

:popcorn:

---

### Post by mikewhatever on 2009-01-11
Not quite sure what you mean, can you provide more info:

1. what kind of HDD, internal/external?
2. what kind of connection, USB/firewire/esata?
3. plug it in and post the output of <sudo fdisk -l>

---

### Post by unimatrix on 2009-01-19
You just need to mount it manually. Don't know why, but it's what I did.

1. Find it with
```
sudo fdisk -l
```
In my case it's called "/dev/sdb1"

2. Make a folder where you want it mounted, for example
```
sudo mkdir /media/wd
```

3. Mount it
```
sudo mount -t auto /dev/sdb1 /media/wd
```
(instead of /dev/sdb1 use whatever you found in step 1)

---

### Post by davidanderica on 2009-09-25
4. Unmount it (maybe?)

```
sudo umount /media/wd
```

(or whatever you named the folder where you mounted in step 2.)



Thanks unimatrix,

I am using LinuxMint Gloria on my laptop and this worked for me.

I was not able to unmount by right clicking on the desktop icon.

After doing a "umount" it read my drive fine and unmounted using the right click menu. 

Thanks again!

---

