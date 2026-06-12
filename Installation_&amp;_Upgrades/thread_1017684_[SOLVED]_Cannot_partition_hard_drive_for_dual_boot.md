---
title: "[SOLVED] Cannot partition hard drive for dual boot XP and ubuntu 8.10"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by kelean on 2008-12-21
I bought a computer on ebay.  Its a dell optiplex P4 3GHZ single core 512 megs memoryand a 80 gig hard drive.  It came with XP installed, but not the install disk.  I am trying to get one.  

I downloaded and burned a fresh copy of Ubuntu fired it up and it ran really great.  I ran the installer and it will not let me free up any space on the hard drive.  It will only let me select the entire HD.  So I got the alternative disk and tried again and it will not work either. 

Next step was to get a copy of gparted.  I fired it up and it will not let me do it either.  I checked and it said that the partition was unmounted.  I did some checking on the forums with no clear answers.  I did install wubi version and it works farlly well but seems slower than it should be.

Any help will be most appreciated, Kelean

---

### Post by ajgreeny on 2008-12-21
> Next step was to get a copy of gparted.  I fired it up and it will not let me do it either.This would always be my first suggestion, but you got nowhere with it so we need to sort out why.

1.  Make sure you have defragged windows a couple of times before you start, having temporarily disabled the virtual swap in windows.  You need to right click on the "My Computer" desktop icon to do that, but then you will need to search for virtual memory in the system settings somewhere, it is so long since I used windows, I can't remember where it is.  That will make sure windows is nicely placed at the start of the drive.

2.  Fire up the live ubuntu CD and go to System > Admninstration > Partition Editor, and try again to resize the windows partition.  If the resize button in gparted is greyed out, right click on the partition and click unmount, if it is there to click, as this could explain the problem.

3.  Resize the windows partition to the appropriate size, make a new partition in the empty space formatted to ext3, shutdown gparted and then go to the install again.

4.  Now when you get to the partitioning part of install choose Manual, then choose the new ext3 partition and install to that, not forgetting you will need a swap partition of about 512 - 1024 MB as well.

All this assumes there really is space on the disk for a ubuntu install, which needs probably about 10GB for a sensible, usable system.

I hope this helps, but if there is still a problem come back again.

---

### Post by 2hot6ft2 on 2008-12-21
> **ajgreeny said:**
> search for virtual memory in the system settings somewhere, it is so long since I used windows, I can't remember where it is.
I believe that would be right clicking on My Computer and selecting properties and you would be looking for environment variables not exactly sure at the moment but it's there in the properties.

Also when you start windows back up after you finish doing your partitioning don't forget to re-enable it.

---

### Post by caljohnsmith on 2008-12-21
In order to get a better idea of your HDD's current partition setup, how about opening a terminal (Applications > Accessories > Terminal), and please post the full output of:
```
sudo fdisk -lu
sudo sfdisk -V
```

---

### Post by kelean on 2008-12-21
I could not find the virtual memory but I did some checking.  I fragmented the hard drive.  Started up the livecd then I started gparted.  I right clicked on hda1 and went to info and here is what I found.

When I choose the paretition and check resize the window pops up but I cannot change anything.  The resize button is grayed out.  I checked and the partition was unmounted.

When I look at the info for the hard drive there are several warning about cluster accounting failed some location: extra cluster in $Bitmap.

There are probably 6 different lines like that.  Now am stumped again.  I can only format the entir hard drive.

---

### Post by kelean on 2008-12-21
Here are the results of the commands you ask to see.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x84aa63ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156248189    78124063+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo sfdisk -V
/dev/sda: OK

```

---

### Post by caljohnsmith on 2008-12-21
Can you still boot into XP OK? How about booting your Windows Install CD, go to the "recovery console" and run:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. Then try again to resize with gparted, and if it doesn't work, please let us know the exact errors you get or even show us with a screen shot.

---

### Post by kelean on 2008-12-21
Yes XP runs fine.  I do not have a install disk.  I was wanting to keep XP on here and dual boot.  I am trying to get an install disk from the party I bought the computer from.

So those are errors on the hard drive it self or the install?

---

### Post by caljohnsmith on 2008-12-21
It would help if you could post the actual errors that gparted gives, or like I mentioned, a screen shot of the errors. How about running gparted by opening a terminal (Applications > Accessories > Terminal) and do:
```
gksudo gparted
```
And then the terminal should show the errors from gparted. Also, since you don't have a Windows Install CD handy, you can instead download and use a Windows Recovery CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). Let me know how that goes.

---

### Post by kelean on 2008-12-21
Here is a screen shot of the info window.  I am going to try the rescue disk you gave me.

---

### Post by meierfra. on 2008-12-21
You don't need any CDs to run chkdsk. In Windows go to  "Start->run" and type "cmd". This opens a  terminal, type

```
chkdsk /r
```  

"chkdsk" will run after your next reboot

---

### Post by kelean on 2008-12-22
Thank you caljohnsmith.  After running chkdsk /r, I ran the alternative install disk.  Ubuntu installed great and without a hitch.

I would like to thank everyone else who helped with my problem.

I am typing this from my new Ubuntu install.  I was correct, this install runs better than the wubi install, seems that way to me.

Once again thanks for all of the help.

---

### Post by caljohnsmith on 2008-12-22
Glad to hear the problem is solved, kelean. Cheers and fun with your new Ubuntu install. :)

---

