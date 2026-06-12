---
title: "Trying to get my HDD to boot again..."
date: 2008-08-17
forum: General Help
---

### Post by sk121506 on 2008-08-17
Alright, I have been searching for answers on the internet and thought it would be easier to get direct help. So I was an idiot and attempted to install ubuntu on the entire windows vista hdd (which i did not want to do). It failed after about 5 seconds into the install for whatever reason that i don't remember. Now when i boot my laptop, i get the pxe-e61 error and it can't find my hdd. What can i do to undo this partition and be able to boot back into vista with all my files? I have been using photorec to backup my files in the meantime, but was curious about using gparted. Seems to simple, but if i deleted the ubuntu partition and then resized the windows partition (i'm guessing to the capacity size?), would I be able to boot into vista? Thanks for any positive suggestions. Let me know if i need to provide any more info.

---

### Post by sk121506 on 2008-08-17
bump

---

### Post by caljohnsmith on 2008-08-18
Try booting up a Live CD, open a terminal, and do the following command:
```
sudo fdisk -l
```
Does that show your Vista partition? Please post the output of that command. If it doesn't, you can try recovering the Vista partition with "testdisk":
```
sudo testdisk
```

---

### Post by sk121506 on 2008-08-18
the output of sudo fdisk -l is:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d702ecc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris
```

is the sda1 my original vista partition, just renamed linux? or what can be diagnosed from just looking at this? i am unfamiliar with using testdisk (though i have used photorec) so if need be, could you please point me in the right direction of how to use testdisk to restore my partition.

---

### Post by caljohnsmith on 2008-08-18
Well, if you were able to recover some of your files with photorec, that's great, because it looks like your Vista partition is indeed completely gone. If you want Vista back you will have to reinstall it I think. I would use the Vista partitioning software to set up all your partitions first, reinstall Vista, and then you can try reinstalling Ubuntu to the partitions you created with Vista.

---

### Post by sk121506 on 2008-08-18
but if i run gparted, i see a huge block of my windows partition, then ubuntu's partition. this is leading me to believe vista is still there. i just don't know how to go about resizing the partition.

---

### Post by sk121506 on 2008-08-18
would i resize the windows partition smaller or larger than it is? do i delete the ubuntu partition and resize the windows to fill ubuntu's partition? sorry for all the questions, just trying to get the most help.

---

### Post by caljohnsmith on 2008-08-18
> **sk121506 said:**
> but if i run gparted, i see a huge block of my windows partition, then ubuntu's partition. this is leading me to believe vista is still there. i just don't know how to go about resizing the partition.
Does gparted actually show an NTFS partition before your Ubuntu partition, or is just labeled as unallocated space? How about attaching a screen shot of the gparted window? I don't see how gparted would see your partitions any different than fdisk, and according to fdisk, your Vista partition is unfortunately long gone.

---

### Post by sk121506 on 2008-08-18
couldnt figure out how to save the screenshot in gparted so i just took a picture of it.

i thot it said windows when i used gparted before, but i was wrong. the only reason i believe it would be possible to restore vista with all the files is the fact that i can find them using photorec. image is attached so let me know your thoughts.

---

### Post by caljohnsmith on 2008-08-18
Since Ubuntu is on your sda1 partition now, it obviously overwrote most of your Vista partition, so I don't think there is any realistic hope in recovering Vista. If I were you, I would just be thankful that photorec was able to recover some of your files. 

If you have the Vista install CD/DVD, I would just wipe your HDD clean, use Vista to repartition it, and then reinstall Vista followed by reinstalling Ubuntu. Or if you want, you could use gparted to shrink down your sda1 Ubuntu partition and create a new partition for Vista. It's up to you.

---

### Post by sk121506 on 2008-08-18
it hurts to hear that. thanks for your help/suggestions.

if anyone else understands my situation and knows of any possible solutions, please let me know!

---

