---
title: "How to partition my HDD?"
date: 2010-10-09
forum: Hardware
---

### Post by smdawson on 2010-10-09
I would like to partition my HDD so that I can dual boot Ubuntu and Win7 and have a shared file space for both OS's. I am working on a laptop that already has Ubuntu installed on it. I have Ubuntu and Win7 on bootable disks.  

I have been reading posts here on the forums and reading through different tutorials on HDD partitioning, although all the different advice has me confused. The fact of the matter is, I don't want to do something stupid (or damaging) because I am not properly informed about this. 

It would really help me if someone could explain what would be the best course of action for the situation I described (and why), the most efficient way of doing it, and then give me very good instructions. :)

---

### Post by rogueleader12345 on 2010-10-10
first off, use gparted.
second, you'll need to resize the partition to allow for others, if your ubuntu partition uses the whole drive
then, you just set the freed space of an ntfs partition for windows and install windows.
however, i recommend installing windows before ubuntu, because the windows bootloader can be touchy

---

### Post by rogueleader12345 on 2010-10-10
also, this link should help a lot: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by smdawson on 2010-10-10
If I need to install windows first, then do I need to format my HDD to clear Ubuntu and then put Win7 on it?

Is recovering the GRUB after installing windows second in the tutorial in the link provided a good idea?

What should the sizes of my partitions be and what filesystem?

I still do not know what a 3rd partition that would share my files between OS's should look like. (size?, filesystem?, partition order?)

---

### Post by smdawson on 2010-10-10
In GParted the "resize" option is not available for my hard drive. Do I need to unmount the drive to be able to resize...?

---

### Post by rogueleader12345 on 2010-10-11
yes, the drive has to be unmounted to resize
as for the shared file space, it would be a good idea to use either a fat32 or an ntfs filesystem, because ubuntu will read both. keep in mind that this "shared" space can be for files only in ubuntu, meaning you can't install applications on it. as for the size, that's really up to you, depending upon how much space you need.
yes, you will have to format the drive. then i would suggest using gparted to create an ntfs partition the size of what you want your win 7 install to be, then install win 7. then install ubuntu using the rest of the unallocated space, with your "shared" partition and your win7 partition already made

---

### Post by smdawson on 2010-10-11
How would I use GParted after I format the drive to size the partitions?

---

### Post by rogueleader12345 on 2010-10-11
an ubuntu or gparted live cd

---

### Post by smdawson on 2010-10-12
Sorry about the last question, it took me 5 minutes after I posted to figure that out. Now I have my live Win7 and Ubuntu cds, time to partition.

---

### Post by smdawson on 2010-10-12
Neither of my boot disks are working...they are DVD -RW. Is that the problem?

---

### Post by rogueleader12345 on 2010-10-12
hmm...don't see why it would be a problem....try reburning them? does it give you any errors?

---

### Post by smdawson on 2010-10-12
I'm not getting any errors. It seems like the computer tries to boot from the disk after I select it, but then just defaults to the HD. Do I need to use a program that is specifically an ISO burner? I just used a regular burning program but I would think it would still work.

---

### Post by rogueleader12345 on 2010-10-12
should have worked, yeah. check your boot order?

---

### Post by smdawson on 2010-10-12
I did that too. Put cd/dvd at #1 and moved HD down to the end. I'm going to get different disks and see if that makes a change.

---

### Post by rogueleader12345 on 2010-10-12
ok, let me know if it works

---

### Post by smdawson on 2010-10-26
Sorry it took me so long, but the new DVD -R disks worked! I was able to format, partition with GParted, and now I have Win7, Ubuntu, and a shared file space. Everything is running smoothly and I enjoy my two OS's and organized file space :)

---

