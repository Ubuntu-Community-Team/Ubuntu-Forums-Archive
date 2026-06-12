---
title: "How Do You Uninstall Ubuntu?"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by CoffeeMaker9000 on 2009-06-17
[COLOR="Red"]***_GO TO PAGE TWO FOR LATEST POSTS_***[/COLOR]

When I installed Ubuntu, I put it on a clean 250 GB HDD, which was a mistake. Now, my Windows HDD has only 800 MB left, and I'm also using an external HDD. I now want to uninstall Ubuntu then reinstall with a smaller partition.

Facts:
-old version of Ubuntu: Feisty Fawn
-the Ubuntu HDD is completely dedicated to Ubuntu and has no other OS on it
-Ubuntu HDD has never been assigned to Windows in the past
-HDD has capacity of 250 GB
-computer has dual-boot
-Ubuntu has no files worth saving
-HDD needed to be recognized by Windows XP after Ubuntu's uninstallation
-Windows (Dell) Recovery Disc is available
-do not want to do harm to the Windows HDD

Objective:
Uninstall Ubuntu and repartition HDD with Ubuntu with only 25GB and Windows with 225GB.

---

### Post by howefield on 2009-06-17
> **CoffeeMaker9000 said:**
> 
Objective:
Uninstall Ubuntu and repartition HDD with Ubuntu with only 25GB and Windows with 225GB.

Boot with the Ubuntu live cd and once the desktop loads, select partition editor from the System > Administration menu.

Delete the Ubuntu partition and resize windows to your required size, then install UBuntu to the free space that you have left.

---

### Post by raymondh on 2009-06-17
> **CoffeeMaker9000 said:**
> When I installed Ubuntu, I put it on a clean 250 GB HDD, which was a mistake. Now, my Windows HDD has only 800 MB left, and I'm also using an external HDD. I now want to uninstall Ubuntu then reinstall with a smaller partition.

Facts:
-the Ubuntu HDD is completely dedicated to Ubuntu and has no other OS on it
-HDD has 250 GB
-computer has dual-boot
-Ubuntu has no files worth saving
-HDD needed to be recognized by Windows XP after Ubuntu's uninstallation
-Recovery Disc is available
-do not want to do harm with the Windows HDD

Objective:
Uninstall Ubuntu and repartition HDD with Ubuntu with only 25GB and Windows with 225GB.

Hello coffeemaker9000,

Back up and save your personal files (windows and ubuntu) someplace first.

You can try gparted to resize/delete the ubuntu partition and then use gparted again to extend windows. If you have ubuntu installed after windows, resizing down (grabbing left and moving to the right) may mess up any ubuntu file (system or personal data) which may mean you may have to do some more work later.

Another option is to delete the ubuntu partition and extend the existing windows ... leaving space for another ubuntu install.  Note, you will have to fix mbr or fixboot the MBR in order to get windows booting as GRUB overwrote unto the MBR.  To fix the MBR, you will need the actual install disk (not the recovery disc) or use supergrub or any other boot tool.

A 3rd option is to re-install windows and be on your merry way with another dual boot set-up with your preferences in size.

I am sure there are a lot more options out there.  Post back what you have decided and we can go from there.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Good luck.

---

### Post by CoffeeMaker9000 on 2009-06-18
But as I said, I don't want to do anything with Windows. I to treat the computer as if a nuclear bomb would explode if I even touch Windows on this operation, except for repartitioning the drive from there. So your (raymondhenson) third option is not really an option. Sorry!

Other than that, all the other ideas on this thread so far are good. Just looking for the one with the easiest, less risky way. I'm not that into code, so any replies after this, pls. consider not having ways related to code.

---

### Post by ToFue on 2009-06-18
> **CoffeeMaker9000 said:**
> When I installed Ubuntu, I put it on a clean 250 GB HDD, which was a mistake. Now, my Windows HDD has only 800 MB left, and I'm also using an external HDD. I now want to uninstall Ubuntu then reinstall with a smaller partition.

Facts:
-the Ubuntu HDD is completely dedicated to Ubuntu and has no other OS on it
-HDD has capacity of 250 GB
-computer has dual-boot
-Ubuntu has no files worth saving
-HDD needed to be recognized by Windows XP after Ubuntu's uninstallation
-Windows (Dell) Recovery Disc is available
-do not want to do harm to the Windows HDD

Objective:
Uninstall Ubuntu and repartition HDD with Ubuntu with only 25GB and Windows with 225GB.



Use cloning software like O&O Diskimage, or CloneDisk to clone your windows drive to external (assuming the external will fit it- you should also be able to boot into the external drive)

Then Clone Only windows partition and once it's running stable use partition editor to resize, adding to the total size of windows, leaving the rest 'raw'..

Then reformat the 'raw' area to ext3, accounting for /home and /swap or whatever part style you prefer w/ the remaining space, and copy linux to it

Feel free to get more opinions..

---

### Post by Hobgoblin on 2009-06-18
> **CoffeeMaker9000 said:**
> 
Objective:
Uninstall Ubuntu and repartition HDD with Ubuntu with only 25GB and Windows with 225GB.

Why not just boot from the Ubuntu liveCD an use partition manager to resize the existing Ubuntu partition.  Then create an NTFS partition in the free space.

---

### Post by CoffeeMaker9000 on 2009-06-25
Hmm, this hard. All of your posts are really good ideas, but having a hard time trying to pick one. I'll wait a little more for more ideas.

---

### Post by raymondh on 2009-06-25
Hi,

Kindly clarify ...

[I]-the Ubuntu HDD is completely dedicated to Ubuntu and has no other OS on it
-HDD has capacity of 250 GB
-computer has dual-boot[/I]

Do you have 2 hard drives in your system?  Or, is one OS in the external whilst the other is in the internal?

---

### Post by CoffeeMaker9000 on 2009-06-25
> **raymondhenson said:**
> Hi,

Kindly clarify ...

[I]-the Ubuntu HDD is completely dedicated to Ubuntu and has no other OS on it
-HDD has capacity of 250 GB
-computer has dual-boot[/I]

Do you have 2 hard drives in your system?  Or, is one OS in the external whilst the other is in the internal?

I have two INTERNAL hard drives, and the one with 250GB (internal) is dedicated solely to Ubuntu. the external drive is not important, just saying that I even need an external drive to keep my files as I'm almost out of space on my Windows dedicated hard drive.

---

### Post by CoffeeMaker9000 on 2009-06-27
> **howefield said:**
> Boot with the Ubuntu live cd and once the desktop loads, select partition editor from the System > Administration menu.

Delete the Ubuntu partition and resize windows to your required size, then install UBuntu to the free space that you have left.

I am now doing it this way and Ill see if it works. Thanks!

---

### Post by CoffeeMaker9000 on 2009-07-16
[B][I][U][SIZE="7"]HELP ME!!!
[/SIZE][/U][/I][/B]
Ok, I already tried repartitioning, but my computer somehow will not let me install Ubuntu again. I repartitioned the drive to 25GB for Ubuntu (already formated for Ubuntu, I forget which one it was) and left the extra 200GB unallocated so I can just partition and format from Windows. But since I couldn't install Ubuntu, I restarted the live CD, but I lost my partition settings that I put it to. So its now back to Square One and I have to figure out how to make the new partitions stay put and to install Ubuntu.

The problem is that I need to get it done quick, or just partition the whole drive for Windows and forget Ubuntu (sorry, Ubuntu fans. although if I do, then I'll occasionally use my live CD for just surfing the web, instead of waiting forever for Windows to boot).

---

### Post by unlimitedz on 2009-07-16
Did you click "Apply" after you did the partition resize?

---

