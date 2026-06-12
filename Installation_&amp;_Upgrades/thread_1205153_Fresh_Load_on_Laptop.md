---
title: "Fresh Load on Laptop"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by Trafficflow on 2009-07-05
I am looking to load Ubuntu on my laptop. I have it on my desktop but I use my laptop all the time!! That way I can teach myself. The OS is Vista and the laptop is a Acer.I have a few questions.
 Which on boots first? And do I just create partitions when loading? A little help so I have it set up correctly would be cool.

  Trafficflow

---

### Post by merlinus on 2009-07-05
You will need to use vista's disk managment tool to resize its partition before installing ubuntu.  But first best to disable paging, reboot, delete pagefile.sys and other temp and unneeded files and defrag several times.

Then you can install ubuntu into the freed up space.

---

### Post by raymondh on 2009-07-05
> **Trafficflow said:**
> I am looking to load Ubuntu on my laptop. I have it on my desktop but I use my laptop all the time!! That way I can teach myself. The OS is Vista and the laptop is a Acer.I have a few questions.
 Which on boots first? And do I just create partitions when loading? A little help so I have it set up correctly would be cool.

  Trafficflow

Helo Trafficflow,

Some reference materials.

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)


As you may have in your desktop, if it is dual-booting, you will have the choice to select OS' to boot first.  To make it automatic, you can edit the menu.lst or download/install startupmanager (from synaptic, terminal or add/remove) and set defaults there.

1.  Defrag Vista (2x if possible)
2.  Back-up your files.
3.  Try out the liveCD and check for defects, MD5Hash and going to livesession, see how it reacts with your system specs' and hardware.  The liveCD is always a good indicator of things to come.
4.  Decide how much you wish to allocate for ubuntu
5.  You can use GUIDED RESIZE in the installer.  Grab the slider (middle) and slide to your preference ... allocating the sizes.  That will do everything automatically.
5.a. You can aslo create the partition/s beforehand and manual install.
- If you do this, use Vista's disk management tool to resize-down Vista.
- Then use Gparted to create the partitions depending on your needs.  At the minimum, you'll need 2 partitions.  Swap at 1.5GB and Ubuntu Root (/) with at least 8-15GB.  Aside from those 2, you can add a separate /home, a /usr, even a /var.  The choice is yours.
6.  You can also use the installer to install on a empty, unallocated space.

A little research and reading goes a long way.  Google is your friend.  Preparation is the key to minimizing troubles in partitioning and installation.

Good luck.

---

### Post by Trafficflow on 2009-07-06
I have a couple questions. The size of the partition should be half of the one hard drive I have installed? What is MD5hash?

---

### Post by Trafficflow on 2009-07-06
Actually I have a good question that I forgot. How should the dual boot work at startup? Will it go right to the os OS or should I have a selection. Can antbody explain?

  Thanks Trafficflow

---

### Post by raymondh on 2009-07-06
> **Trafficflow said:**
> I have a couple questions. The size of the partition should be half of the one hard drive I have installed? What is MD5hash?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

As for the partition size ... it really depends on your requirements for windows and Ubuntu.

Most get by with having 8-15GB for ROOT.  Add to that SWAP size and ... personal files such as media, data, etc. etc. ...you see what I'm getting at?  My ubuntu is a full-use system and I have allocated 100GB for it.  As of to date, I only have used about 60GB (inspite/despite of numerous songs and videos).

When you use the Vista tool to shrink your vista partition, it will recommend the minimum size for Vista.  If that is OK with you, then go for it ... realizing that you only have so much space for this OS and so many for that OS.

Remember to defrag before shrinking Vista (or windows for that matter)

Good luck

---

### Post by Trafficflow on 2009-07-06
I understand all the points you have made.I am taking my time 
  so I do this correct, now that the 4th is over. I am confused
  about what it should look like after the install. Can you explain?
  
  Thanks Trafficflow

---

### Post by raymondh on 2009-07-06
> **Trafficflow said:**
> I understand all the points you have made.I am taking my time 
  so I do this correct, now that the 4th is over. I am confused
  about what it should look like after the install. Can you explain?
  
  Thanks Trafficflow

You will have (thru GRUB) a text based window that will allow you to choose the OS of your choice.  The first few options (starting from the top) will be KERNEL (generic), KERNEL (recovery), memtest (memory test) and then Windows.  If you have more than one kernel, it will also be listed in the same order :

KERNEL A (generic)
KERNEL A (Recovery)
KERNEL B (generic)
KERNEL B (Recovery)
Memtest
Windows 

For the kernel ... it will be listed as 2.6.28-11 (as an example).  You will normally boot-up to a generic kernel unless you need to do recovery work.

Initially, Ubuntu will be the default OS and you will be given 8 seconds (roughly) to choose another OS (windows).  To pause the countdown, you normally will give the spacebar a tap and then use the arrow keys to highlight what you wish to boot up into.  Once chosen, the operating system then boots up.

Simple yet very effective and powerful ... GRUB is as a bootloader.

Hope this answers your question.

---

