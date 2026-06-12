---
title: "How can I unformat a HDD to bring back Windows?"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by ianzdad on 2009-02-24
My teenaged son installed Ubuntu on a second HDD on my Win XP computer then, when trying to format an external drive, he accidentaly formatted the main Windows hard disk. As this disk contains access to email accounts, hundreds of family photos, GCSE and A level course work etc. it needs to be restored it to the original Windows XP state. Is there any way to roll this back  using a reliable tool that will not cause any more damage? What sort of costs am I looking at? Any suggestion glady received!

---

### Post by ouija on 2009-02-24
Good luck.  Look up "data recovery" in your local phone book, and be prepared to shell out some coin if you really want to try and recover your data -- and even at that you aren't going to get everything back..

---

### Post by thamaraj on 2009-02-24
Try to use PC Inspector File Recovery software to recover you file

---

### Post by Partyboi2 on 2009-02-24
You might have some success with [[COLOR=Blue]testdisk[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk") and it is free, you can also download it from the ubuntu repo.

---

### Post by caljohnsmith on 2009-02-24
I would recommend starting with "testdisk" as Partyboi2 all ready mentioned, because it might be able to restore your Windows partition so that you won't have to resort to low-level data-digging programs in order to recover your files. To use testdisk, first boot your Ubuntu Live CD, choose the "try Ubuntu without making changes" option, and once you get to the Ubuntu desktop, download the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop. Then open a terminal (Applications > Accessories > Terminal) and do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also if any of the partitions seem to be your lost Windows partition based on the directory listing. Also, in the terminal again, please post the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by az on 2009-02-24
Testdisk won't help.  Your partitions probably weren't changed, just formatted.  The filesystem is gone.

You can try to use file carving to recover lost files.

Photorec comes with testdisk and works well.

Don't install it from source, it's in the repositories.  Boot the live cd, plug in an external drive onto which you will save your recovered files (you can'T recover them in place) and run sphotorec:

sudo apt-get install testdisk

cd /media/disk/recoveryfolder

sudo photorec /dev/sda1

(The above assumes the recovery folder in in /media/disk/recoveryfolder and the source partition is sda1.  Change them to whatever they need to be.

File carving will recover most of your files, but will generate a lot of file fragments that you will need to sort through.  Good luck.


See here:

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

---

### Post by ianzdad on 2009-02-25
Thanks for all of the suggestions. At least it looks as if I might recover something. I'll have a go when I've got a free 1/2 day on the weekend (may be a couple of weeks till that happens) - I'll let people know how I get on.

Further suggestions still welcome.

---

### Post by GizmoTheGreen on 2009-02-25
if you can access the disc in another windows machine try recuva, from piriform, its free and form the creators of ccleaner and defraggler.

---

