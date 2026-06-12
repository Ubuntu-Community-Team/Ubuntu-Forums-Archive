---
title: "Install as second OS failed, now option gone."
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by mid_life_crisis on 2009-01-19
I tried installing Ubuntu as the second OS on a Vista Home Premium laptop, but the partioning app seemed to freeze, and after several minutes of absolutely no activity, I cancelled it (actually had to hard shut down the laptop).  When I restarted, it no longer gave the option to install Ubuntu as a second OS, but only by using the entire hard drive.  Is there a file or directory I can delete somewhere that will straighten this out?

---

### Post by taurus on 2009-01-19
Before you resize your windows partition, you should boot into windows and defrag your harddrive a couple of times.

---

### Post by mid_life_crisis on 2009-01-19
> **taurus said:**
> Before you resize your windows partition, you should boot into windows and defrag your harddrive a couple of times.

Thank you, this sounds like good general advice that I should have thought of myself (doh!).  I don't see how it will fix the problem I am currently experiencing, though.

---

### Post by taurus on 2009-01-19
Are you using the LiveCD (desktop CD) or the alternate CD?  Which release are you trying to install?

---

### Post by mid_life_crisis on 2009-01-19
> **taurus said:**
> Are you using the LiveCD (desktop CD) or the alternate CD?  Which release are you trying to install?

The DVD has copies of several versions of Ubuntu.  I am booting from the DVD and selecting "Ubuntu" 8.10 and then the option to install it.  I have been able to more or less run the OS from the DVD, with one major problem that does not appear to be correctable unless I install the OS, as it requires changing to a wireless driver other than the one that normally runs off the DVD.  Once I am satisfied that I can get the wireless working (I have another thread open for that) I will probably just dump Windows completely (I have a desktop machine for that) and run Ubuntu as the only OS on the laptop.

---

### Post by mid_life_crisis on 2009-01-22
When the computer starts, it offers a boot menu with Ubuntu as one of the choices, but Ubuntu does not start and the HD does not appear to have been partitioned.  How should I go about finishing this process?  I would really like to have the option to run the current release other than in a VM.  
The DVD menu has stopped offering the option to partition the disk and install Ubuntu as a second OS.  It now wants only to take the entire drive.
Any suggestions?

---

### Post by MobiusCoffee on 2009-01-22
When I partitioned my drives, I did it from Vista.  Vista's partioner is pretty easy to use and it wont get mad at you fo using it.  I'd suggest creating a new partition from inside Vista, then using the new partition to install Ubuntu.

If you don't know how to find the partitioner on Vista, I believe you can find it in start menu>computer right click on computer>properties(I think?  It's been awhile since I've been on Vista) Then somewhere in there is the partitioner.

---

### Post by mid_life_crisis on 2009-01-22
> **MobiusCoffee said:**
> When I partitioned my drives, I did it from Vista.  Vista's partitioner is pretty easy to use and it won't get mad at you for using it.  I'd suggest creating a new partition from inside Vista, then using the new partition to install Ubuntu.

If you don't know how to find the partitioner on Vista, I believe you can find it in start menu>computer right click on computer>properties(I think?  It's been a while since I've been on Vista) Then somewhere in there is the partitioner.

Good suggestion, thank you.  I just hope it isn't one of those options that is only on the Business versions.
Any ideas on how to clean up the boot menu mess?  At this point I seem to have a boot option that has no partition to point to.  If I create the partition, is there a way to direct the existing boot entry to it?

---

### Post by MobiusCoffee on 2009-01-23
You don't need the business version of Vista to use the partioner.  So, don't worry ^^

Once you reinstall Ubuntu on the new partition, you can just overwrite the old boot loaer and it shouldn't be a problem anymore.

---

