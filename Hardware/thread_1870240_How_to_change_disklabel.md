---
title: "How to change disklabel?"
date: 2011-10-26
forum: Hardware
---

### Post by Miqi on 2011-10-26
I recently screwed up my dual boot with a windows 7 install disk. After much research and work, I can boot windows again, but I still can't access my ubuntu partition. I've tried live booting off CD and usb, but the disklabel isn't recognized. The best i can get is EasyBCD bios extender to tell me it's called "HDA partition 2" and fdisk -l to say there is an ntfs and a linux partition on the hard drive. I think if I change the ubuntu partition name to sda1 it will work, but I'm afraid to go about this without being sure I won't make things worse.

What should I do?

---

### Post by wolfen69 on 2011-10-26
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by diasf on 2011-10-26
a liveCD boot, followed by a chroot to your drive and update-grub didn't solve it?

---

### Post by Miqi on 2011-10-27
Nope. I even made a live usb of live-disk-repair trying to reinstall grub on my laptop, but the problem is to any live media, my hard drive is an unallocated mass of 320 gigabytes. I used a windows program to modify the mbr so a grub option was added, but it goes straight to grub rescue because it can't find the files in a place it recognizes. It says the only device is hd0, and it doesn't have any partitions. I know I have to rename my hard drive to fix this problem, I just want to know how to do it without making everything worse (i.e. not being able to boot at all).

---

### Post by diasf on 2011-10-27
I removed the grub from mbr a couple of times, updating grub always worked. You do not need to rename the drive, you just need to set the names correctly on grub. Usually, it does that by itself, but you can change manually to match your system as well.

---

### Post by Miqi on 2011-10-27
That's not my problem. I can't reinstall grub because nothing but windows can access the hard drive. I tried installing it through EasyBCD, but that takes me to grub rescue.

---

### Post by Miqi on 2011-10-27
However, knowing how to change it manually might be useful

---

### Post by fdrake on 2011-10-27
```

man e2label
man tune2fs

```

---

