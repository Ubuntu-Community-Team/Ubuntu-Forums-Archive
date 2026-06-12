---
title: "latest update. Now can't find /dev/hda1"
date: 2008-07-16
forum: General Help
---

### Post by bobosity on 2008-07-16
Ran the latest update this morning and I accidentally told it to use new menu.1st. I usually keep the old one. Now the boot just hangs. I got into and found that it can't find /dev/hda1.

Next, I fired up a puppy livecd and checked. The new menu.1st points to:

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

hda1 is correct. (I think)

there is no backup menu.1st
recovery mode does the same thing. Ditto for the older listed kernels.

Any ideas?

---

### Post by enchesss on 2008-07-16
Have a go at this:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by bobosity on 2008-07-16
Well, that seemed to work... until it didn't.  The splash screen hangs for awhile then comes up initramfs can't find /dev/hda1. 

/dev/hda1 is there. I'm now on the 7.10 livecd and I can see the whole drive.

---

### Post by bobosity on 2008-07-16
is it possible that my problem lies in fstab? I've had problems there before when loading another distro. Right now it reads:

# /dev/hda1
UUID=1a6180cf-f126-4e40-b2f6-50797e4b40e1 /               ext3    defaults,errors=remount-ro 0       1

Is there something I can do here?

---

### Post by alfalfa31 on 2008-07-16
You could try making sure that UUID is actually the right one...

```
sudo vol_id -u /dev/hda1
```

---

### Post by plucky on 2008-07-16
I am wondering if the device designation has changed from /dev/hda1 to /dev/sda1,in which case the grub cannot find the location of the root partition as you have > kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/hda1 ro quiet splash the root partition as /dev/hda1


Try changing that line to ```
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=1a6180cf-f126-4e40-b2f6-50797e4b40e1 ro quiet splash
``` assuming the UUID for the root partition is correct.

You can check that by using the command ```
sudo blkid
```


Good Luck

---

### Post by bobosity on 2008-07-16
Thanks I was looking for a command like that. Unfortunately it matches my fstab. 

I remember seeing my menu.1st having a line like that once
root=UUID=1a6180cf-f126-4e40-b2f6-50797e4b40e1 Something like that. 

now it reads root=/dev/hda1

Is this a clue?

---

### Post by alfalfa31 on 2008-07-16
> **plucky said:**
>  assuming the UUID for the root partition is correct.


That is true, as my hybrid setup now calls what would normally be considered /dev/hda, /dev/sdc

if you run 

```
sudo vol_id -u /dev/hda1
```

and you get 

```
/dev/hda1: error opening volume
```

odds are that on running blkid, you'll note that the device you're looking for isn't there anymore and has been replaced by an exact replica under a different name (like the hard drive witness protection program).

---

### Post by alfalfa31 on 2008-07-16
> **bobosity said:**
> Is this a clue?

I'd say it is, so long as /dev/hda is no longer referenced...

---

### Post by bobosity on 2008-07-16
SOLVED!

Thanks Plucky that was the key and thank you everyone who replied

---

### Post by drs305 on 2008-07-16
Looks like I'm too late!

Run this to see what your system calls the partitions:
```
sudo fdisk -l
```

Then check fstab for your root partition:
```
 cat /etc/fstab | grep " / ext3"
```

If the address uses the '/dev/XXXX' convention, make sure they match.
If they don't, make fstab agree with fdisk:
```

sudo cp /etc/fstab /etc/fstab-backup
gksu gedit /etc/fstab
```

If fstab uses UUIDs, make sure the fstab UUID matches the "sudo blkid" results.

---

