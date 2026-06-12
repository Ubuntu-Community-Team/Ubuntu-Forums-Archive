---
title: "Need help!New to Ubuntu."
date: 2008-09-13
forum: General Help
---

### Post by Phillip91 on 2008-09-13
I got a virus that wiped my HD when I had Windows and I installed Ubuntu so it would hopefully not happen again.Well I guess the disc was messed up and it wouldn't install properly.It ended up installing 4 times.I need to find out how to delete the ones I don't use.But first I need to find out which ones I don't use.Also,I have 50 gigs between my 2 Hd's and it's only saying I have about 30.Did I screw up the partitioning part?



Help Appreciated,
      Phillip91

---

### Post by WRDN on 2008-09-13
When you installed, did you create new partition(s) for each Ubuntu installation? If so, wait for the GRUB menu (that appears at bootup) and select the installation that works. Now, press "e" while the entry is highlighted, and one of the lines of text will read:

> root (hd0,4)

Note that this will probably be different for you. The first number (0) refers to the HDD number, and the second (4) refers to the partition. Now, boot from the LiveCD, open GParted and delete any partitions you no longer want.

You can also list the partitions in Ubuntu by opening the Terminal and typing:

```
sudo fdisk -l
```

---

### Post by kokkus on 2008-09-13
If you formated your HDs and installed ubuntu and choosed to install it on the whole disk everything else you don't use is already deleted.
So now you can try to recover back text, picture and MP3 files etc. if you miss them.
I suggest you go to synatic package manager (system>administrator)
Search for testdisk, install it and then open Root Terminal (applications > system tools) 
Then type photorec.
Photorec is a part of testdisk that can find back formated and lost files tha thasn't been overwritten by other files.

Hope this helps you.

---

