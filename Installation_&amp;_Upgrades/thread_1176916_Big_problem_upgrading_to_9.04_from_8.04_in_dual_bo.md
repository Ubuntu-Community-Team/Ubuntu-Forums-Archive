---
title: "Big problem upgrading to 9.04 from 8.04 in dual boot system"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by pritcharded on 2009-06-02
My PC has three hard drives sda (160GB), sdb (320GB) & sdc (320GB). It had XP installed on sda and when I first installed 8.04 the installer script automatically installed it on sdb. Both systems worked well.
I recently attempted to upgrade to 9.04 by first installing 8.10 via CD and then using the network to move to 9.04 as per directions. 
In the course of doing this I foolishly assumed that as I had a standard dual-boot installation, the upgrade would automatically preserve my dual-boot arrangement.
When the partition editor opened the dialogue asked if it should use the whole disc. As 8.04 is on its own disc (sdb) I said yes. I didn't get a warning saying this will also wipe sda but maybe it's happened as now I can no longer access XP.
I've attached some screen shots. The file browser indicates that of sda only 6.4GB is available and I'm hoping that means the remaining 150GB is still NTFS and my Windows files. On the other hand Gparted suggested something else.
In addition there is a major problem with the way 9.04 loads (presumably with the Grub script). For some reason the screen won't activate (meanwhile I can enter my user name and password and it clearly installs the OS). The only way I can get it to start is to keep starting in safe mode and running thru the available options. By this means it starts eventually (but I'm not sure what sequence repeatably does the trick).
Synaptic Package Mngr doesn't show any defective packages. Running apt-get update hasn't solved the problem.
Detailed help with this would be very much appreciated as it's well above my limited expertise.

Ted Pritchard

---

### Post by quixote on 2009-06-03
eep. This does not look hopeful.  It looks like it formatted sda to an ext3 (linux) filesystem.  Data on that drive might still be recoverable with a direct read method, but that's deep-in-the-weeds tech stuff and your files won't be pretty.  *Might*.  It's a longish shot.  If you have something really important on there that you can't live without, it would be worth it.  In that case, do *not* use the drive.  Every time you use it, more of the old data is overwritten.

If it's not life-or-death files, or if--even better--you have a backup, then I'd say just chalk it up to a learning experience.  You'll waste less time starting from scratch.  (And, next time, I guess, pay very careful attention to where it thinks it wants to put your new OS :/ )

But first, make sure that you know for certain what's what among your various drives.  Maybe your windows is still hiding in there somewhere.  It's not clear from the desktop screenshot or GParted.  What are those 2 extra USB drive icons?  Why are the sizes of the drives mostly different from what they should be?  All of sdc is an ntfs (windows) drive.  Could it maybe have renumbered the drives somehow, and decided what was sda is now sdc??  If so, the only problem would be that grub isn't pointing to the right place, and that should be easy to fix.

Can you post the output of ```
sudo fdisk -l
``` 

That's "l" as in list.  fdisk stands for "format disk" so don't tell it to do anything except "list"!

---

### Post by pritcharded on 2009-06-03
quixote,

Thanks for helping.

fdisk -l shows this:

ted@ted-desktop:~$ sudo fdisk -l
[sudo] password for ted: 

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18657   149862321   83  Linux
/dev/sda2           18658       19452     6385837+   5  Extended
/dev/sda5           18658       19452     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         773     6209091    7  HPFS/NTFS
/dev/sdb2             774       38913   306359550    5  Extended
/dev/sdb5             774       37589   295724488+  83  Linux
/dev/sdb6           37590       38913    10634998+  82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000082

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS
ted@ted-desktop:~$ 

Since I last posted I think I've managed to fix the start-up problem by reinstalling Grub. 
Wrt recovery you may well be right. Gparted "help" refers to recovering partition tables with a utility called "testdisc" available from here; [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Have you any experience with it?

Once again thanks for your help - I'm in a bit of a bind with this.

Regards, Ted

---

### Post by quixote on 2009-06-03
When you say "fix the startup problem" I assume you mean that jaunty boots normally?  Your Windows partition is still in limbo somewhere, right?

Testdisk is a great program.  I've used it successfully three times and love it.  Bit intimidating, text-based, but essential.  It can be installed via synaptic if the universe repository is enabled.  Their documentation is here: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk).  [Screen shots]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") of partition recovery.  A simpler but less visual step-by-step for partition recovery is [here]("http://www.howtoforge.com/data_recovery_with_testdisk").

I think the first thing I'd try to do is see what, exactly, is on those ntfs partitions you have: the 6GB sdb1, and all of sdc1.  Boot into jaunty, mount those drives (clicking on them in the file manager, ie nautilus, will mount them) and see what's on them.  I'm still hoping that sdc1 turns out to be your windows drive!

---

### Post by pritcharded on 2009-06-04
Quixote, thanks for your ongoing help.
Re boot problem I spoke too soon. Despite the fact that last night I rebooted 9.04 several times last night without difficulty, this morning my boot problem was back! 8.04 boots OK everytime.
I'm sure Windows was in its own partition (~150GiB in size) on sda (160 GiB). Ubuntu was (and still is) on sdb. My third disc sdc has backups on it. File manager nows shows sda to only be 6.4GiB in size (with only 65.0MB used) and not 160 GiB. Because of this I think there must be a good chance that my Windows partition remains untouched - albeit invisible.
I have installed TestDisc and will see what I can find.
As long as the Windows partition is in fact undamaged I may be able to recover by loading my XP system disc and trying a Windows repair. Presumably that would overwrite Grub. I could then reinstall 8.04 or 9.04 using the dual boot option.
Thanks once again for your help
Regards, Ted

---

### Post by pritcharded on 2009-06-04
Quixote
I've had some success. Using TestDisc I found all my Windows files and have been able to copy them successfully successfully. I will now try to recover the NTFS boot sector.
Regards, Ted

---

### Post by quixote on 2009-06-05
Ted-
Yes, it will remove grub from that location, but, unless you'd prefer a clean install, you don't have to reinstall just for that.  

Rebuilding grub isn't difficult.  Instructions specifically for rebuilding after a windows install are here, about 4/5 of the way down: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)  

It'd be less time-consuming if you've already customized your previous install.  (Settings, other programs, etc.)  If not, a new install would probably be more straightforward.

---

### Post by pritcharded on 2009-06-06
Quixote
All is well again. I opted to do a complete clean install for both XP and 9.04. Both are now working perfectly. I used a CD copy of 9.04 this time (I had previously used the 8.04 to 8.10 to 9.04 upgrade approach) and there is a very clear warning as to what happens if the "use whole disc" option is selected. Unless the scripts are different for each installation route, I can only assume I must have had a "senior's moment" at a most inopportune stage.
All's well that ends well so thanks once again for encouraging me to try TestDisk - without it I was in for serious grief.
Regards, Ted

---

### Post by quixote on 2009-06-06
The installation script is the same, but the cryptic linux disk names don't help.  

I'm glad that testdisk helped!  

Cheers,
quixote.

---

