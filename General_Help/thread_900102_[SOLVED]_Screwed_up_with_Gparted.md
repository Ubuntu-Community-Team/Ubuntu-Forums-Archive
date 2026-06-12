---
title: "[SOLVED] Screwed up with Gparted"
date: 2008-08-25
forum: General Help
---

### Post by yessirsir on 2008-08-25
Guys, i have a 60GB Hard drive and i installed ubuntu on it...after updates and everything it was about 5GB (little less) of used space. so i loaded the live session re re-sized the partition to like 7GB but i accidentally canceled the process :S (not good) 

So now the hard drive partition is 55GB big (it says used space 55GB) but i know it use only about 5GB i saw it b4 the process starts. 

and i cant re-size it the way i wanted it anymore ...im stuck with a big 55GB partition that cannot be shrinked down more than 55GB.  

There is now also 2 other small partition apart from the big 55GB one. 

I would like to know if im really screwed there and i need to re-install everything from scratch (re-install ubuntu + do updates ...so on) or there is a way to revert back or something .. like go back to the way it was at the beginning.  i would hope that its possible for the computer to realize that there is really only 5GB used on that hard drive so i could get the rest of free space into a new partition  (which should be 55GB) 

curse this cancel button arrgg 

anyone could help here ?

---

### Post by coffeecat on 2008-08-25
You don't actually say, but I presume you can't boot up the hard drive installation. Is this correct? If this is so, it's possible the partition table is corrupted. No doubt an uber-hacker could fix this by hand, but that's way beyond me.

If you boot up with the live CD, can you connect to the internet with it? Because I'm going to ask you to post the output of a terminal command, which you won't want to transcribe by hand, and post a screenshot.

From the live CD, open a terminal and post the output of:

```
sudo fdisk -l
```That's a lower-case L, not one. Now Open Gparted (System > Administration > Partition Editor) and post a screenshot of the Gparted window.

**Edit:** you say you were resizing the Ubuntu partition to 7GB. What were you trying to do? Were you wanting to reinstall Windows or add another distro? It might be worth clarifying this in case you need to reinstall so that you can get suggestions about partitioning.

---

### Post by yessirsir on 2008-08-25
no my ubuntu still boots fine from the HD and also i can connect to the net from whichever way i boot (live or from HD) but im stuck with a drive with used space of 55GB instead of the real 5GB of used space. 

i was trying to format the rest unused space of that partition to NTFS not for installing Windows (i gave up wanting using windows once i saw how great ubuntu is :P) but to format it to NTFS in order to save the files i had backed up on another NTFS drive (which is not mine so which is why i need the extra space to copy the stuff on the rest of my HD)

ok ill go ahead and load that command now + paste ya a screeny. ill still use the live session i guess.


heres a screenshot of GParted

[http://img383.imageshack.us/my.php?image=56222675hw0.png](http://img383.imageshack.us/my.php?image=56222675hw0.png)


heres the terminal screenshot

[http://img383.imageshack.us/my.php?image=55624705nb3.png](http://img383.imageshack.us/my.php?image=55624705nb3.png)


Btw u will see on the screenshot that the undo button is available, but its not going to actually undo the problem im talking about, i did the check option after i rebooted (which did nothing) so if i click undo now it wont revert back to my original partition, it would only undo the check scan thing that Gparted did this time ...but the undo option from the time i clicked cancel during the re-partitioning process is defenitly gone.


Man i should have noticed the Undo button b4 restarting, after i clicked by mistake on cancel :S   i think it would have been fine... but since it was a live session nothing saves ..so the undo was now greyed out ...couldnt click it anymore.

---

### Post by gatenby_jp on 2008-08-25
Recommend re-installing and instead of allowing the installer to use whole disk select manual partitioning ... delete all existing partitions then create a partition of say 7.5 gigs (although i recommend a minimum of 15) select mountpoint as / create your ntfs partition and create a manual mount point say /ntfs remember to leave some space for a swap partition ... At the end of the day it will cost less time than trying to fix

---

### Post by yessirsir on 2008-08-25
@gatenby_jp

I understand and this is what i would do, but investing time for this problem is not what bothers me. to tell you the truth, id rather fix this without re-installing because if i did re-install, that would mean that i need to also re-download updates and apps that i need again and unfortunately my internet provider restricts my bandwidht ... i cant download much in a month or they charge me so much more if i go over my limit :(

---

### Post by sandysandy on 2008-08-25
the new ubuntu will release in Oct 08. u can place advance order for free copy a few weeks in advance from shipit. 

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

[http://www.ubuntu.com/getubuntu/countdown](http://www.ubuntu.com/getubuntu/countdown)

regards

---

### Post by gatenby_jp on 2008-08-25
This was used in a similar case some time back

so try looking at this
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I think your partition table was corrupted and this is possibly a means of fixing

Having read a few more things I think testdisk exists on your live cd

---

### Post by -Zeus- on 2008-08-25
before reinstalling, I suggest you run fsck (similar to chkdsk in windows).  To do this, press Alt+F2 and type "sudo touch /forcefsck".  then reboot your pc and it will run a filesystem check

---

### Post by yessirsir on 2008-08-25
=D>omg fixed it !!!=D>

Thankx a whole lot guys

---

