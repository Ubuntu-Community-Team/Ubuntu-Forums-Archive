---
title: "Ext4 manual partition help"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by 311005901 on 2009-05-14
I am trying to reformat my harddrive (now running Intrepid on ext3) and run Jaunty on ext4.

I go to step 4 in my installation and select "Specify partitions manually."

Then, I tried to make:
sda1 117127MB ext4 from ext3
sda5 2903MB swap

The partition then says there is no root filesystem.

What is going on? All I did was change the format and it spits the error back. Could someone tell me what I need to do?

---

### Post by alphacrucis2 on 2009-05-14
> **311005901 said:**
> I am trying to reformat my harddrive (now running Intrepid on ext3) and run Jaunty on ext4.

I go to step 4 in my installation and select "Specify partitions manually."

Then, I tried to make:
sda1 117127MB ext4 from ext3
sda5 2903MB swap

The partition then says there is no root filesystem.

What is going on? All I did was change the format and it spits the error back. Could someone tell me what I need to do?

As the partition already exists then you may have to delete it and then recreate it as an ext4 partition.

---

### Post by x33a on 2009-05-14
you aren't specifying a mount point for root. there should be an option in the partitioning window, for a mount point.. set it as root.

---

### Post by 311005901 on 2009-05-14
> **alphacrucis2 said:**
> As the partition already exists then you may have to delete it and then recreate it as an ext4 partition.

I did that also.
The error message said the same thing.

> **x33a said:**
> you aren't specifying a mount point for root. there should be an option in the partitioning window, for a mount point.. set it as root.

Ok. So I set the ext4 as root and the swap as swap?

---

### Post by alphacrucis2 on 2009-05-14
> **311005901 said:**
> I did that also.
The error message said the same thing.



Ok. So I set the ext4 as root and the swap as swap?

ext4 mountpoint should be /

Some people recommend dividing the available space into two partitions (plus swap), one for / and another one for /home. That way you keep all your user data on a separate partition to the os files.

---

### Post by 311005901 on 2009-05-14
> **alphacrucis2 said:**
> ext4 mountpoint should be /

Some people recommend dividing the available space into two partitions (plus swap), one for / and another one for /home. That way you keep all your user data on a separate partition to the os files.

Woahwoahwoah. I'm really confused.

The partition editor in the installation process doesn't seem to give me all those options.

It just says:
/dev/sda
-/dev/sda1  ext3  117127 MB
-/dev/sda5  swap  2903 MB

The column under "mount point" for both is blank.

---

### Post by alphacrucis2 on 2009-05-14
> **311005901 said:**
> Woahwoahwoah. I'm really confused.

The partition editor in the installation process doesn't seem to give me all those options.

It just says:
/dev/sda
-/dev/sda1  ext3  117127 MB
-/dev/sda5  swap  2903 MB

The column under "mount point" for both is blank.

Assuming you just want one ext4 partition then first delete the ext3 partition. Then recreate the partition from the freespace as an ext4 partition and set the mountpoint of the new ext4 partition to /

---

### Post by x33a on 2009-05-14
format sda1 to ext4. set mount point as root.

set mount point of sda5 as swap.

---

### Post by alphacrucis2 on 2009-05-14
> **x33a said:**
> format sda1 to ext4. set mount point as root.

set mount point of sda5 as swap.

You are right. He doesn't have to delete the partition. Right click and reformat should do it.

---

### Post by 311005901 on 2009-05-14
> **alphacrucis2 said:**
> Assuming you just want one ext4 partition then first delete the ext3 partition. Then recreate the partition from the freespace as an ext4 partition and set the mountpoint of the new ext4 partition to /

> **x33a said:**
> format sda1 to ext4. set mount point as root.

set mount point of sda5 as swap.

Oh mai. Thank you kind sirs. Installing like a charm.
:popcorn:

---

### Post by 311005901 on 2009-05-15
Bing bong.
I think the FS is corrupt.

When I try to use several programs at a time, it locks up completely and I can't even shutdown. I have to pull out the laptop battery for it to go down. When I have the opportunity to click "Shut Down," the attatched image appears. (It's blurry... Sorry)
[[IMG]http://img17.imageshack.us/img17/9319/wot.th.jpg[/IMG]](http://img17.imageshack.us/my.php?image=wot.jpg)

---

### Post by x33a on 2009-05-15
list of options you can try:

1. check your ram with memtest (grub menu).

2. run fsck on root using live cd.

did the install go perfectly, or were there any glitches?

---

### Post by 311005901 on 2009-05-21
The install went perfectly, but I reformatted to reiserfs.
Hopefully it works!

---

