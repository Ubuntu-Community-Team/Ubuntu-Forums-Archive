---
title: "Moving to a larger Drive"
date: 2008-11-10
forum: Hardware
---

### Post by tommygunner on 2008-11-10
I'm running out of hard drive space and posted recently about moving to a new, larger drive.

I've used dd to copy the old hard drive:

dd if=/dev/hda of=/dev/hdb

This worked great except that I still have the same partition size afterwards. I've tried resizing in Gparted but it won't resize it.

I've also tried using resize2fs to resize the partition but this didn't work.

I followed this instructions here: [URL="http://www.howtoforge.com/linux_resizing_ext3_partitions"]http://www.howtoforge.com/linux_resizing_ext3_partitions
[/URL]

I changed from ext3 to ext2 then tried to resize. Afterwards I'm still left with 40GB usuable partition on an 80GB drive.

I was thinking that the method above would be the best method to use for moving to a new drive because it would avoid having to mess with GRUB stuff.

Does anyone know how I can do this?

---

### Post by caljohnsmith on 2008-11-10
You could use Ubuntu's partition editor gparted to simply copy the entire partition over; I would do it from the Live CD so you don't have to worry about anything being mounted. After it is copied over to your new HDD, you should be able to resize it. After that, you would of course need to install Grub to the MBR of the new HDD; to do that just boot your Live CD, open a terminal, and do:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If you decide to give it a shot, let me know how it goes.

---

### Post by tommygunner on 2008-11-10
Well, the problem with Gparted is it will not let you resize any partition. When I have copied the main partition, it doesn't allow me to resize it. I am using a pretty recent version of Gparted also.

I can resize other partitions but not the one with all the data on it. The program doesn't show it as an available option for it.

---

### Post by caljohnsmith on 2008-11-10
> **tommygunner said:**
> Well, the problem with Gparted is it will not let you resize any partition. When I have copied the main partition, it doesn't allow me to resize it. I am using a pretty recent version of Gparted also.

I can resize other partitions but not the one with all the data on it. The program doesn't show it as an available option for it.
So are you running gparted from the Live CD with System > Admin > Partition Editor? And if there are any swap partitions on the HDD in question, do you select them and choose "swapoff"? I don't understand why gparted won't let you resize a partition that you have copied over with gparted; it's been a while since I've fooled with my partitions, but gparted let me resize my partitions when I needed to. How about posting a screen shot? Does it show the resize function as greyed out or something?

---

### Post by tommygunner on 2008-11-10
Yes, I'm using Gparted live CD version 3.9-4. I can resize the swap partition. It creates various unallocated partitions under the swap partition.

I then go to the primary partition which has all of the data and try to resize it. The maximum size still shows as the current size even though I have about 40GB of unallocated space available.

I've resized partitions before with Gparted, splitting my ntfs partition and adding a ext3 one. However, with ext3 resizing has been giving me problems.

---

### Post by tommygunner on 2008-11-10
I created an ext3 partition from the unallocated space and am now copying and pasting this empty partition into the main one. I'll let you know if it works.

---

### Post by tommygunner on 2008-11-10
I copied and pasted the newly created ext3 partition to the main partition and the partition is still there afterwards. I'll post a screen shot later.

---

