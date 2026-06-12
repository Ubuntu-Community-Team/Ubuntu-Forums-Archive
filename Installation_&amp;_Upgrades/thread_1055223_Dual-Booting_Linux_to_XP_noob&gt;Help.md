---
title: "Dual-Booting Linux to XP noob&gt;Help"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by tuknic on 2009-01-30
I apologize if this thread I am posting is posted elsewhere. I looked for some time but to no avail.

At this time I have a 150g IDE hard drive installed onto a Dell desktop. It is not partitioned and is running Ubuntu completely by itself.
A little background, I previously had a hard drive running Windows XP and when the computer turned on it was quite noisy. Sometimes it was very loud. Thinking that this HD had it's days numbered I decided to purchase a new HD. Originally thinking I would obtain a copy of Norton Ghost and just copy it to the new hd. But after some time I decided to go with Ubuntu. This hd is sitting in my closet with anti-static wrapping.
I now have another 250g hd (a 3rd now). I want to install this hd into my desktop. I am also wanting to dual boot windows XP and Ubuntu. 
Now this is where I start to get confused and am not quite sure what I'm doing. I guess I have more questions than how do I do this. Such as;
- Do both OS's need to be installed onto the same HD?
 - If so should they be on the larger of the two HDs?

-If I can have the XP on one hd and Ubuntu on the other will I need to be having a certain order when connecting to the MOBO?

-What of BIOS?

-If partitioning is involved with this process I have no knowledge or previous experience doing this. How would I be doing this?

Of course I don't expect a lengthy explanation step by step how to perform this task. Any links would be helpful. I have just had a difficult time finding the proper thread. Seems like most threads are concerning XP to Linux. What of Linux to XP? I would appreciate any assistance with this. Thank you.

---

### Post by dstew on 2009-01-30
If you want to have a dual-boot machine, with both Linux and XP, you should install XP first, then Linux. I assume you will install Ubuntu.> Do both OS's need to be installed onto the same HD?
No. But XP likes to be on a primary partition, and usually it should be on the master disk if you have a master-slave setup. Sometimes your BIOS wants to boot only a master disk.> If so should they be on the larger of the two HDs?You can put them anywhere that they fit.> If I can have the XP on one hd and Ubuntu on the other will I need to be having a certain order when connecting to the MOBO?Generally it is good to use the master disk if you have two disks on one controller. But, if you have two controllers, either OS can be on either controller, or both on one.> What of BIOS?The BIOS needs to be set to boot the disk that has grub installed on it (in a dual-boot system). Grub can then boot a linux system or Windows system on another paritition or even another disk.> If partitioning is involved with this process I have no knowledge or previous experience doing this. How would I be doing this?I like to partition a disk before starting the installation process. You can make a [Gparted live CD]("http://gparted.sourceforge.net/livecd.php") that has a good partitioner on it. You can also use the partitioner that runs in the Ubuntu installation CD. It works the same (and probably is the same program) as the Gparted Live CD. Sometimes, though, users panic a bit at the partition step, and abort or mess up the installation. I always feel calmer parititioning before installing.

[Psychocats]("http://www.psychocats.net/ubuntu/installing") has a very good page for installation in a dual-boot setting.

---

### Post by opscure on 2009-01-30
You can do it on two separate HDs if you want.  Install windows to your second one and configure grub (/boot/grub/menu.lst) to check the second HD for Windows. 

There should be an example for a windows config already in the commented part of the menu.lst file...  ie
```
 title		Windows 95/98/NT/2000
 root		(hd0,0)
 makeactive
 chainloader	+1

```

You would just change the hd0,0 to the drive and partition of the windows install (likely hd1,0)

When you go to install Windows make sure that you install it to the correct drive.  Also, make sure that the linux drive is the master when you get everything done, as grub will need to be detected off of boot.

Good luck.

---

### Post by tuknic on 2009-01-30
I failed to mention something. I do not have a start-up or recovery disc for XP. I had planned on ghosting it onto the newer 250g HD. 
So I should finish the installation of XP. Then install Ubuntu?
I apologize for the noobish'ness of my questions but everyone has to start somewhere and I would much rather do this myself than have someone pay to do it and learn nothing.

---

### Post by avtolle on 2009-01-30
I would finish the XP install and then install Ubuntu. That way, Grub will see the XP install, and (hopefully) configure itself so you can dual boot.

---

### Post by dstew on 2009-01-30
> So I should finish the installation of XP. Then install Ubuntu?Yes, make sure you have a stable, working XP install before you install Ubuntu. When you partition, you have to be careful not to delete the XP partition, since you don't have a recovery disk.

When you install Ubuntu, you need to install the grub boot loader. You should install it into the Master Boot Record of whatever disk has Ubuntu on it, assuming your BIOS can boot that disk. If Ubuntu and Windows are on the same disk, you should let the grub boot loader install into the MBR of that disk.

The grub installation will not damage the Windows system. It only puts itself into the Master Boot Record, which is the first sector of the disk. Since the MBR is not part of any partition, grub cannot harm the Windows system.

Sometimes, you will have trouble booting Windows after you install grub. Usually this is a configuration problem that can be fixed. If worse comes to worse, and you want to get rid of grub and Ubuntu, there are ways to restore a Windows boot loader to the MBR without having a Windows Recovery Disk. The [Supergrub disk]("http://www.supergrubdisk.org/wiki/UninstallGRUB") can do that, I think.

---

