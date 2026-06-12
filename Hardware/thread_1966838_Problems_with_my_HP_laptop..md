---
title: "Problems with my HP laptop."
date: 2012-04-27
forum: Hardware
---

### Post by Gotestra on 2012-04-27
So recently, I decided to give Ubuntu a shot. I installed it on my C drive, along with Windows 7, and well, I loved it more than I had imagined. But I'm facing like a bunch of problems which if not addressed, prevent me from switching to Ubuntu.

So firstly, some info. Hay I'm Gotestra, 13 and from India but none of you probably want to know that. I installed Ubuntu on my C drive and gave it 10GB. I got 4 GB DDR3 RAM, 320 GB 7200RPM HDD and a 1.2 Ghz Dual Core processor. Its an HP laptop by the way.

I'll just cut to the chase now. These are the problems I'm facing:

1) I can't use the right click button on my trackpad. To right click, I have to click on the trackpad with both my fingers, i.e a two finger gesture. I just want to use the click button. Its a synaptics trackpad.

2) HP set me up with keyboard shortcuts to increase and decrease brightness, F3 and F2 respectively. When i use them in Ubuntu, that little pop up comes up indicating that brightness is being reduced or increased. But despite that, the brightness does not go down or up in reality. Its very annoying as it drains power much faster on battery.

3) I got a drive called My Stuff on Windows. The drive letter is Z:. The file system is NTFS and its a dynamic disk. I use it for my movies, music, pictures etc. The problem is, I can't access it in Windows. It gives me an error saying it couldn't mount. 

4) And finally, I didn't expect to actually want to switch to Ubuntu. But then, one cannot anticipate the future very accurately. Now, I want to keep on using Ubuntu instead of Windows. I wanna keep Ubuntu on separate partition, and Windows on C:/, as usual. I found this tutorial:
[How to Migrate]("http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-migrate-updated-for-release-1204.html")
I updated to that new version that released today(Solved the problem where I couldn't left click and drag something with my trackpad). Would the tutorial work with this new version?

Eagerly waiting on replies.

---

### Post by bcbc on 2012-04-27
Yes the migration works.

No, you shouldn't run linux on a drive with dynamic disks. These are only visible to Windows, and therefore allowing the partitioner to split your drive will likely result in data loss. Even using Wubi with dynamic disks is not a good idea, in my opinion. (It only works if you install on a partition that is physically in the MBR partition table, but there's still a chance that you could damage the dynamic partitions or the data contained therein.

---

### Post by Gotestra on 2012-04-27
> **bcbc said:**
> Yes the migration works.

No, you shouldn't run linux on a drive with dynamic disks. These are only visible to Windows, and therefore allowing the partitioner to split your drive will likely result in data loss. Even using Wubi with dynamic disks is not a good idea, in my opinion. (It only works if you install on a partition that is physically in the MBR partition table, but there's still a chance that you could damage the dynamic partitions or the data contained therein.
But I don't have any other drive, and I wanna keep using Ubuntu [IMG]http://thebotnet.com/images/smilies/okay.png[/IMG]

---

### Post by Gotestra on 2012-04-28
Bump this thread.

---

### Post by bcbc on 2012-04-28
In general the advice given on this forum is to convert your dynamic disks back to normal and then use an extended partition with multiple logical partitions instead (recognized by both Windows and Linux).

Microsoft recommends deleting and recreating all partitions when converting from dynamic (they make it easy to convert to dynamic, but not from). But I've heard the EaseUS partition manager can do it. If you go this route you should merge the truly dynamic partitions back to the ones in the partition table, and backup data just in case.

If you intend to use Ubuntu predominantly then you should move away from a Wubi install when you're ready, either by installing fresh or you could [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") the wubi install if you want to keep things setup the same way as they are now.

---

