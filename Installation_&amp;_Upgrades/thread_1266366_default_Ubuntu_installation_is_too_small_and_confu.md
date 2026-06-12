---
title: "default Ubuntu installation is too small and confusing!"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by hhhiker on 2009-09-14
The standard installation of Ubuntu is confusing, because :

[LIST]
[*]it chooses the minimum space for itself (2.5 GB) as a default mode, so it becomes impossible to install anything else later on !!  Trying to part it later is an illusion for a newbie to the system. **Who would expect a non usable default mode!**
[*]Also choosing the minimum room pushes the cursor to the far right of the display (may be not the case before, but now with tera disk it's stacked on the right), so we don't even see that there is a cursor and something after it!
[*]The colors meant to be different are brown and another sort of brown almost the same! Great, and I am not color blind, I pass all the tests!
[*]The control-dialog-graph is just below the button "Specify partition manually (advanced)", so it looks like the control-dialog-graph is just for the advanced part, so many users may chose not to touch it to avoid some sort of advanced pitfalls and hop they'll get an extra-small Linux.  Also that control is exactly tuned like the static image of disk space above, therefore it reinforce its static look!
[*]Ok the size is written, but it's written just below the advanced advanced part so many beginner block that information! + dev/sda3 is not meaningful for any beginner, reinforcing the advanced assumption!
[/LIST]

- So I think the first correction to do would be to stack the cursor in the middle of the available memory so not doing anything works and the different part are more obvious!
- The second thing would be to make sure the bottom graphical-control does look associated with all options and not only with the advanced one.
- Third thing : meaningful colors.
- 4th : some flexibility about parting the disk with the live CD parting tool removing is alright, but impossible to do anything with the free "sectors" except to put them back where they were!


I finally manage to install Ubuntiside side by side with Vista, but I had to reinstall Vista twice, yes Vista on the top to erase everything! This mainly because I did not see the size trick!

A screen picture is below, a bit small but it's still understandable, the gliding cursor is just above the mouse button :   [http://hhhiker.blogspot.com/](http://hhhiker.blogspot.com/)
[IMG]http://2.bp.blogspot.com/_azz0VQHG8nU/Sq6Mkm83vvI/AAAAAAAAAAM/F-toqRWaPtA/s1600-h/confusing-ubuntu-installation-interface.jpg[/IMG]

---

### Post by carlosgs91 on 2009-09-14
.

---

### Post by steveneddy on 2009-09-14
Since you are very inexperienced with advanced computer software capabilities, try partitioning the drive in Windows beforehand.

Then during the Ubuntu installation point the installer to the newly created partition.

If a desktop, you may consider installing another hard drive, one for Windows and one for Ubuntu. 

There is no need to make something as elementary as partitioning a hard drive difficult. Research online about partitioning before you actually attempt the partitioning yourself.

If at first you don't succeed, try try again.

EDIT:

You may also try the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php") so that you can partition any HD without the need for an operating system installed.

After partitioning, of course, install any operating systems.

Have fun!

---

### Post by hhhiker on 2009-09-14
> **steveneddy said:**
> Since you are very inexperienced... 

Thanks, I am fine now, Thanks! I like Linux and I am using it right now, but I think this specific interface should be improved !!!!!!!!!

---

### Post by mudeye on 2009-09-14
I just put U9.04 as a dual boot on my Dell XP and found the same "too small" result.  Looking around, it appears that some of the CDs were improper and were sent without having enough space for U to work well.  And then I found that one should not re-partition a mounted drive--which U is when you are "on" U.   I also must keep XP for some apps.

Q: With the U9.04 CD, can I first erase the existing U OS that I now have on my hard drive, and then install U9.04 with, say, 10 GBs?

---

### Post by mikewhatever on 2009-09-14
> **mudeye said:**
> I just put U9.04 as a dual boot on my Dell XP and found the same "too small" result.  Looking around, it appears that some of the CDs were improper and were sent without having enough space for U to work well.  And then I found that one should not re-partition a mounted drive--which U is when you are "on" U.   I also must keep XP for some apps.

Q: With the U9.04 CD, can I first erase the existing U OS that I now have on my hard drive, and then install U9.04 with, say, 10 GBs?

Yes, that's the way to go.

> **steveneddy said:**
> Since you are very inexperienced with advanced computer software capabilities, try partitioning the drive in Windows beforehand.

Then during the Ubuntu installation point the installer to the newly created partition.
.....

Can Windows now create ext3 partitions? Last time I checked, it called ext3 unknown file system.

---

### Post by alienclone on 2009-09-14
> **mikewhatever said:**
> Can Windows now create ext3 partitions? Last time I checked, it called ext3 unknown file system.

im probably wrong but i think if you are using windows to create a partition for linux you have to  just create the blank partition (like unallocated or something) then when installing linux you select the blank partition and format it the the ext2,3,4 of your choosing.

---

### Post by hhhiker on 2009-09-14
> **mudeye said:**
> I just put U9.04 as a dual boot on my Dell XP...  In my case the CD (very last distrib 9-09 64) were perfect, the same CD worked fine when I realized I had to move this EVIL LITTLE BUTTON toward the left.

By the way what's the risk of Vista interfering with Ubuntu ?  Installing service packs seems odd, already just because it boots several times and if not attended will reboot on Ubuntu insted of itself!

---

