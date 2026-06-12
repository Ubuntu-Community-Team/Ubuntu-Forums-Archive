---
title: "How to set up to run Vista 64 &amp; ubuntu without losing programs"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by theCrave on 2009-02-22
I have read through a good bit of this forum and not found a clear answer.  I have a laptop running on vista 64, I want to be able to boot in either vista 64 or ubuntu.  I understand how to do this with the live disk.  

My question is this, How do I install ubuntu to a partition without losing any applications that I use on windows?  In all of the tutorials it says to back up all important data.  But, I can't just back up photoshop, visual studio , expressions etc. to a flash drive and have them work again.  The disks I have for all for all of these programs are one use only.  I can not afford to lose any of these applications.

Please tell me how I can achieve the goal of being able to boot in either OS, and not worry about losing any of my important applications.

Thanks in advance...

---

### Post by whoop on 2009-02-22
you are advised to backup because any operation could theoretically lead to data loss. So although you should not worry that you will lose data you will never be 100% sure that you won't.

Anyway, to install ubuntu:

Determine what size you want for your vista and what size you want for ubuntu. Once you got that figured out install windows vista (if you have not done so allready) on the unpartitioned drive (windows will take up the entire drive). If you have been running windows for a while defragment you windows partition (this will speed up partitioning later).
Once you are done boot the ubuntu live-cd; go to terminal and type:
```

sudo gparted

```

In gparted resize the windows partition to make room for ubuntu.
Now you have a windows partition and some unpartitioned space.
Do a (optional) reboot to check if windows vista is still working (just to feel secure)
Now boot the live-cd again and start installing ubuntu. When you get to partitioning just tell it to use the unpartitioned space.

That's it.

---

### Post by Mark Phelps on 2009-02-23
You said your laptop is already running Vista 64 and you emphasized the need for NOT losing anything in the process of installing Ubuntu.

Ok, two things to be very careful about ...

1) Partition resizing.  Despite claims to the contrary, do NOT use GParted or the Ubuntu installer to resize the Vista OS partition to make room for Ubuntu.  Doing this runs the risk of corrupting the Vista OS boot, and should that happen, unless you have a Vista DVD handy to boot into and run Startup Repair, your Vista installation is then permanently unbootable!  For a link on hints for workarounds to the Vista disk management tool shrinking problems, see below:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

2) Installation.  Make sure you do not choose the "use entire disk" option for installing Ubuntu.  This will do exactly what it says -- wipe your partitions (including Vista), repartition the drive, and install Ubuntu on it.

Also ... If you're really anxious about losing your Vista stuff (and given your investment in apps and time, I don't blame you), I would recommend that you invest $50 in a third-party MS Windows-based backup product like Acronis True Image or Paragon Disk Manager and back off the Vista OS to an external drive.  That way, if the worst happens, you will be able to restore your Vista OS.

---

