---
title: "Need help to recover from botched installation"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by jheis on 2009-08-18
I did a dual boot install of 9.04 on a T43 Thinkpad with a 80 GB drive and everything seemed to go fine. XP in a 25 GB partition & Ubuntu in a 50 GB partition.
 
After the install I also installed some software packages with the add/remove tool. Again, everything seemed to go fine.  I was then prompted to also install some updates.  I installed all the updates *except* those relating to Evolution since I was intending to use Thunderbird instead of Evolution.

Apparently, this was a BIG mistake because now when I try to launch Ubuntu - instead of the log in screen - I get a reddish flash across the top of the screen and 4 columns of narrow alternating black & white horizontal stripes filling most of the rest of the screen.  Fortunately, XP still works...

How can I recover from this?  TIA. 

James

---

### Post by jheis on 2009-08-18
Bump.  Anyone?

---

### Post by pizza-is-good on 2009-08-18
Since you only used Ubuntu for a day, I just recommend that you do a clean install of Ubuntu.
 
My reccomendation is that you ALWASYS check ALL updates, just in case, although I doubt that it was those updates that caused your system to crash.
 
If you need tips on the reinstall, let me know.

---

### Post by presence1960 on 2009-08-18
> **jheis said:**
> I did a dual boot install of 9.04 on a T43 Thinkpad with a 80 GB drive and everything seemed to go fine. XP in a 25 GB partition & Ubuntu in a 50 GB partition.
 
After the install I also installed some software packages with the add/remove tool. Again, everything seemed to go fine.  I was then prompted to also install some updates.  I installed all the updates *except* those relating to Evolution since I was intending to use Thunderbird instead of Evolution.

Apparently, this was a BIG mistake because now when I try to launch Ubuntu - instead of the log in screen - I get a reddish flash across the top of the screen and 4 columns of narrow alternating black & white horizontal stripes filling most of the rest of the screen.  Fortunately, XP still works...

How can I recover from this?  TIA. 



James

Boot your machine, at the GRUB menu choose recovery mode. Be patient as all the text scrolls on your screen- let it finish. Choose fix x from the menu, you may have to scroll down to see it. When that is complete choose resume normal boot and see what happens.

---

### Post by jheis on 2009-08-19
Well, I tried running xfix in the recovery mode and now instead of the 4 columns of black and white stripes I'm getting the red flash at the top of the screen a couple of green & purple streaks across the middle of the screen and a corrupted bottom half of the "Windows is shutting down" screen...  Seeing "Windows" gave me a bit of a start fearing that Ubuntu had trashed the XP partition as well, but XP still works.

I've also tied dpkg & fsck with no luck.

I'm ready to try a new install, but the Ubuntu installation program wants to install along side the two existing OS (XP & 9.04).

So, I need help.  How do I uninstall the corrupted Ubuntu & do a fresh install.

James

---

### Post by raymondh on 2009-08-19
> **jheis said:**
> 

So, I need help.  How do I uninstall the corrupted Ubuntu & do a fresh install.

James

James,

2 options :

1.   On partitioning stage, select manual.  _*Highlight the appropriate partition*_ as your ubuntu may be installed inside an EXTENDED partition, set the mountpoint root (/) and format to either ext3 or ext4.  This will rewrite over the old 9.04.

2.  You can boot into the liveCD and go in live session to access gparted (system > admin > partition editor. In gparted, click on swap and select swap-off.  Then, use gparted to delete the old 9.04 leaving the space unallocated.  Exit gparted and continue with the install ... selecting (use available free space -something to that wording).

You can also use this opportunity to create a separate /home partition for future re-installation issues.

Whatever you choose ... have your files backed-up first.  Post back if you are unsure or need more assistance.  Remember ... during the install,  you have a chance to back-off until step 7.

If unsure, post a screenshot of gparted and we can go from there.  It'll help the forum visualize the install.


Good luck.

---

### Post by jheis on 2009-08-19
I followed Raymond's instructions & used gparted to try to fix the problem. 

I was able to delete the botched 9.04 installation & left the 50 GB partition unallocated.  

When I ran installation again, however, it expanded the XP partition & gave me tiny partitions for 9.04.  I'll try to attach a screen shot of what I've got now in gparted:

What now?  I don't want to screw things up worse than they are.  Thanks

James

---

### Post by drs305 on 2009-08-19
Check out Post #11:
[http://ubuntuforums.org/showthread.php?t=1244519#11]("http://ubuntuforums.org/showthread.php?t=1244519#11")

It will provide a brief explanation and then direct you to a post of how to repeat the installation, avoiding the same problem. The partitioning Step 4 has tripped up a lot of new users - hopefully it will be fixed.

---

### Post by raymondh on 2009-08-19
> **jheis said:**
> I followed Raymond's instructions & used gparted to try to fix the problem. 

I was able to delete the botched 9.04 installation & left the 50 GB partition unallocated.  

When I ran installation again, however, it expanded the XP partition & gave me tiny partitions for 9.04.  I'll try to attach a screen shot of what I've got now in gparted:

What now?  I don't want to screw things up worse than they are.  Thanks

James

Drs' has a good guide about the 2.5GB install error.

You can elect, at this point, to work and resize what you've got or, re-do.

[This is a link on a similar situation]("http://ubuntuforums.org/showthread.php?t=1241878&page=3").  In this thread, the OP decided to re-do and create partitions beforehand and then use the manual install option.  If you decide to follow this route/thread, note that XP's disk utility will not shrink hence requiring that you use gparted, or another utility.

Post back if you need clarifications.

Good luck.

---

### Post by jheis on 2009-08-19
Thanks Raymond & Drs

I guess third time is charmed.  After reading through everything, I decided to delete the tiny partitions & start over.  The corrupted screen still flashes once before it goes to the login screen, but it *does *go the the login screen, so I guess I can live with it.

Attached is a screen shot of gparted as it is set up now.  Let me know if you see any problems with it.  Thanks again.

James

---

### Post by drs305 on 2009-08-19
jheis,

that looks good - and you have plenty of space in your ubuntu partition should you ever decide to split it up to create a few more logical partitions such as a separate home or data partition.

---

### Post by raymondh on 2009-08-19
> **jheis said:**
> Thanks Raymond & Drs

I guess third time is charmed.  After reading through everything, I decided to delete the tiny partitions & start over.  The corrupted screen still flashes once before it goes to the login screen, but it *does *go the the login screen, so I guess I can live with it.

Attached is a screen shot of gparted as it is set up now.  Let me know if you see any problems with it.  Thanks again.

James

Well done James =D>

Congratulations ... enjoy your install .... happy ubuntu-ing.

---

