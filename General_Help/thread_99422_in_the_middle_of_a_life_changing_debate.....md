---
title: "in the middle of a life changing debate...."
date: 2005-12-05
forum: General Help
---

### Post by Llewxam on 2005-12-05
k, since i got ubuntu installed on my laptop (hard drive's 20 gigs) and i got a dual boot to keep winblows which has greatly screwed with my hard drive space, i want to take out the winblows partition without compromising ubuntu and the many settings i've made for it since i got it 'cause it would really suck having to go through all that again. 
so herein is my debate: how can i take out the winblows partition and merge the space to the linux partition without taking out ubuntu and not have some file fragmentation complications? anyone that can help me on this one is more than welcome and is more than appreciated.

---

### Post by Bachstelze on 2005-12-05
run fdisk -l and post the results here, we'll see if you can do this without reformating everything.

---

### Post by Llewxam on 2005-12-05
Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1922    15438433+   7  HPFS/NTFS
/dev/hda2            1923        2432     4096575    f  W95 Ext'd (LBA)
/dev/hda5   *        1923        2432     4096543+  83  Linux

---

### Post by Haegin on 2005-12-05
I'm by no means an expert in this and haven't tried similar but as far as I know you should just be able to format the windows partition as ext3 or whatever filesystem you use on linux and then just mount the new space as something like /home/llewxam (assuming you dont already have a folder there) then copy your home directory accross to it. Then edit the fstab so it mounts the new partition as your home directory (then you can delete the old home directory and use the space for something else).

As far as I am aware this will get you using the space previously occupied by windows as your home directory.

Please someone correct me if I am wrong (and confirm if I am correct as well - I like being right...)

---

### Post by dodger on 2005-12-05
yep, this should work. and it has it's uses, too.

having /home on a different partition greatly reduces the hassle of a reinstall. ( should you ever tweak your system into oblivion ;)

---

### Post by Llewxam on 2005-12-05
:confused: i just want to delete winblows and merge the partition to the linux one... obviously first gotta copy my music files and pics and stuff i have in windows.

---

### Post by jnoreiko on 2005-12-05
merging isn't really possible. You have to delete one and then extend the other.
Without a second drive to copy things to temporarily, you can't do that.

---

### Post by Llewxam on 2005-12-05
[QUOTE=jnoreiko]merging isn't really possible. You have to delete one and then extend the other.
Without a second drive to copy things to temporarily, you can't do that.[/QUOTE]
well ... i do have 2 desktop pc's i can copy the files i don't want to lose.

---

### Post by Nu-Buntu on 2005-12-05
You really don't have to merge them. Since Linux has a unified file system rather than drive letters, just mount the reformatted space and use it. It should show up once you have edited your fstab and created a folder for the partition in /media.

---

### Post by Llewxam on 2005-12-05
k well i'll get to that. thanks.

---

