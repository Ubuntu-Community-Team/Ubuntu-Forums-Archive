---
title: "Error Formatting Flash Drive"
date: 2016-12-31
forum: Hardware
---

### Post by shane_faulkinbury2 on 2016-12-31
I'm trying to format my 3 month old flash drive and I get an error writing to ```
/dev/sbd:input/
```
Does anyone know how to fix this?  I got an error trying to format it in Windows to with no explanation of course!  :D

---

### Post by #&amp;thj^% on 2016-12-31
More information please.
Are you just trying to blank it?(Write zeros to it)
What format are you trying to use. (Fat/FS or Ext4/3/2)

---

### Post by shane_faulkinbury2 on 2016-12-31
I just click on the little gear icon, select to over write everything, select FAT and click start twice.  maybe I should try my terminal?

---

### Post by #&amp;thj^% on 2016-12-31
sudo fdisk -l to see what is the dev name of the partition. 
We assume that is /dev/sdb1 
From terminal write 
```
sudo umount /dev/sdb1 
```
```
sudo fsck.vfat -f -p /dev/sdb1
```
That "should" now create a Fat file system...Change the drive"sdbx" to yours of of course

---

### Post by shane_faulkinbury2 on 2016-12-31
It's not sbd1.  Is there a command to list the ports?

---

### Post by #&amp;thj^% on 2016-12-31
You did not read my post...or I did not explain clear enough...issue this and paste back:
```
sudo fdisk -l
```

---

### Post by shane_faulkinbury2 on 2016-12-31
Well that command showed them all and so did ```
lsblk
``` However neither show the 16 GB flash drive.  It does however show in Disks!

---

### Post by #&amp;thj^% on 2016-12-31
> **shane_faulkinbury2 said:**
> Well that command showed them all and so did ```
lsblk
``` However neither show the 16 GB flash drive.  It does however show in Disks!

Yuk!! that's not good!
If disks shows it...maybe gparted might be more useful here...as I like it better than the Disk Utility. 
So you could try and install Gparted and use that to partition your thumb drive.
```
sudo apt install gparted
```
I will hang in here for a bit to see how you are making out.

---

### Post by shane_faulkinbury2 on 2016-12-31
I already had GParted installed and had tried that earlier, but like the two terminal commands the flash drive is not listed on it either.  Maybe it's time to trash it?

---

### Post by #&amp;thj^% on 2016-12-31
Well did you try to change the drive in the top right hand side of gparted
See Screenshot
If Disk Utility see's it I got to believe Gparted will also

---

### Post by shane_faulkinbury2 on 2016-12-31
I sure did and I get no drop down so I would assune only my HDD is listed?.

---

### Post by #&amp;thj^% on 2016-12-31
Sometimes I have had great success (About 90%) downloading gparted as a iso and burning it to a CD then boot to the CD.
Download: [http://distrowatch.com/table.php?distribution=gparted](http://distrowatch.com/table.php?distribution=gparted)
And Plug the USB Thumb Drive and Try that way.
Where your Thumb Drive is only 3 months old its worth a shot.

---

### Post by sudodus on 2016-12-31
Have you tested the drive in another USB port and in another computer?

If still no luck, and you cannot see it with lsblk or with Windows, I am afraid that it is damaged beyond repair. See this link for more details: [Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by shane_faulkinbury2 on 2016-12-31
Thanks both of you for trying to help.  I think I'm going to try the GParted ISO idea and if that doesn't work just trash it.  Anyone seeing this I have to say Kingston flash drives are crappy!  This is my second one to fail out of a batch of three and I have never had flash drives fail at such a rate as Kingston.  :frown::rolleyes::evil:

---

### Post by #&amp;thj^% on 2016-12-31
Good Luck..:) And I agree with your views on Kingston ;)

---

