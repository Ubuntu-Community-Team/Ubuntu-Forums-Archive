---
title: "Mount NTFS, doesen't have a valid NTFS"
date: 2008-11-02
forum: General Help
---

### Post by dollzii on 2008-11-02
Trying to mount my old windows NTFS partition on new Xubuntu install. 

> 
sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19fd19fc

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1023 8217243 54 OnTrackDM6

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4aa24aa1

Device Boot Start End Blocks Id System
/dev/sdb1 1 4929 39592161 83 Linux
/dev/sdb2 4930 4998 554242+ 5 Extended
/dev/sdb5 4930 4998 554211 82 Linux swap / Solaris 

> The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around? 

---

### Post by taurus on 2008-11-02
Here is something for you to look over.

[http://ubuntuforums.org/showthread.php?t=385218&page=3](http://ubuntuforums.org/showthread.php?t=385218&page=3)

---

### Post by dollzii on 2008-11-02
Now, i've read every thread i could find on the OnTrack subject.
Everybody says the same; 

> /dev/hdb1 * 1 1653 833111+ 54 OnTrackDM6

Adapt your bootloader and add the option hd<x>=remap63 for your kernel where x is your disk.

Now reboot your system and the partition is visibale as (for example)

/dev/hdc1 * 1 826 832576+ 6 FAT16

Here is my /boot/grub/menu.lst

> ## ## End Default Options ##

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            8f816516-dd92-4903-8d63-a509d2b66e63
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=8f816516-dd92-4903-8d63-a509d2b66e63 ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            8f816516-dd92-4903-8d63-a509d2b66e63
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=8f816516-dd92-4903-8d63-a509d2b66e63 ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            8f816516-dd92-4903-8d63-a509d2b66e63
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


What line do i need to edit?

---

### Post by Marturion on 2008-12-16
dollzii, I had similar trouble with an old Win98 disk that had OnTrackDM6, I actually just blogged about it, with the step by step solution to how I did it yesterday.

[Shameless plug]("http://www.escapetradition.com/2008/12/ontrackdm6-and-me.html")

Ultimately, for you, it sound like you'll want to reformat the drive to something more Linux friendly, like ext3

If there's data on the drive you want off first, and you want to use the <drive>=remap63 solution to mount it, you'll have to use an older version of Ubuntu from a LiveCD (or some other live CD that has a kernel that still responds to the remap option). 

The kernel changed, and the remap option is now obsolete. (For good sounding reasons that smarter Linux people then me understand.)

[I found a little bit of info discussed here]("http://kerneltrap.org/mailarchive/linux-kernel/2008/3/11/1137834/thread#mid-1137834")

To directly answer your question, if you have an older version of Ubunutu already running somewhere, the line you want to edit is the first one that looks like this 

```
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=8f816516-dd92-4903-8d63-a509d2b66e63 ro quiet splash
```

you should place the hd<x>=remap63 at the end of that line, after "splash" (In my case it was hdd=remap63)

Hope this helps!
-Dan

---

