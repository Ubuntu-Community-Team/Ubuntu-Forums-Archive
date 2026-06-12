---
title: "Restoring grub\ error finding stage1"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by SCUEY on 2009-06-10
Hello,

I have Windows XP installed on my internal drive.  A while ago I installed Ubuntu on my external hard drive.  Grub, I found out, was on my external drive, and I needed my external drive to be turned on in order to boot to either Ubuntu or Windows.

Recently my external hard drive broke.  Now I cannot boot to either OS.  I am working from the live CD.  I looked through the forums and started following directions from this thread: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but I ran into a problem.

When I ran "find /boot/grub/stage1" it told me "Error 15: File not found."  I assume this is because the location it is looking for is on my external drive.

So I'm wondering what the best and safest solution is to this problem.  I just want to be cautious and not make the problem worse.

My goals are either to setup GRUB so that it's on my internal hard drive or to return to booting using my BIOS.  Right now I just want to be able to boot to Windows so that I can back up my files (yes, I can mount my internal drive now, but I'd like to boot to it too.).  Then I can later set up a dual boot system.

Thanks!

---

### Post by merlinus on 2009-06-10
Boot from xp disk, select restore (or repair), and then fixmbr (or repair boot sector).

---

### Post by SCUEY on 2009-06-10
If by "xp disk" you mean the Windows XP CD, I don't have one.  I only have "recovery disks" that were created with some HP software sent with my computer.  Do you think those would work the same way?  From my understanding, they have something to do with the recovery partition that was created on my internal hard drive.  I will put one in and see what happens.

---

### Post by SCUEY on 2009-06-10
OK, I put in the restore disk and it told me that my personal files would be saved but my programs would be erased.  I would have to reinstall them.  I accidentally hit "next" and it went through the process.  I didn't want to do that, but it turned out just fine.  It looks like it returned me to the last system restore point.  So that's OK.  I'll just have to install a few things.

Thanks anyway!  Even though I didn't really do what you said, it reminded me of my restore disks.

---

### Post by merlinus on 2009-06-10
Glad it worked for you!  Post back if you run into any other problems.

---

