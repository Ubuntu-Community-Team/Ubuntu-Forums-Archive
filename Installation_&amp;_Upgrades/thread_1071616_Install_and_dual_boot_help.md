---
title: "Install and dual boot help"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by mavrick70004 on 2009-02-16
SO i am totally new to Linux and wanted to do a dual boot with my windows xp. i have windows xp on a Sata drive and i wanted to put linux on a second hd i had lying around which is a 20Gb Ide. Everything works fine in Windows so i know there is nothing wrong with my drives. so i put in the cd during windows and chose the option "Demo and full installation". after restart nothing happened and it booted right into windows, i then got a message about how ubuntu will change something in my boot menu so i accepted and rebooted again this time i had a choice of Windows xp or Ubuntu, i chose ubuntu and installed it on the 20gb ide Hard Drive and everything seemed to go ok until i rebooted, the ubuntu boot menu would try to start up but i would get a error 21 and then nothing i tired switching all the stuff in the bios and still nothing. so this time i tried removing the Xp Hard drive and installing with the CD but the computer will not recognize the ubuntu CD that is in the drive and i just get a drive boot failure, but my windows xp cd will boot up just fine can someone tell me what im doing wrong?

---

### Post by mikewhatever on 2009-02-16
The most common problem with cds not booting is that people burn the iso as data or create a bootable cd. Please review the guide below and make sure you've burnt it correctly.
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by caljohnsmith on 2009-02-16
It sounds like you did a Wubi install (Ubuntu inside Windows), but since you are giving Ubuntu its own drive anyway, I would suggest doing a standard Ubuntu install to its own partition. You can do that by selecting the "try Ubuntu without making changes" option when you boot the Ubuntu CD, and then double-click the installer icon on the Ubuntu desktop once you get to the Ubuntu desktop. That will allow you to install Ubuntu to its own partition. Here is a guide you might find useful:

[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html)

Good luck and let me know how it goes.

---

### Post by mavrick70004 on 2009-02-17
the problem was that i had Winzip set up to handle .iso so when i downloaded the ubuntu and saw the winzip icon i ASSUMED it was a .zip file so i extracted to a folder and then burnt to a cd, i tend to work to fast sometimes so that problem was fixed but i posted another problem im having if you guys know anything about that problem it would be great i still have no linux up and running and im getting tired of trying :\

---

### Post by Roi des Belges on 2009-03-09
Hi all,

I kinda have a rather different issue to this. I don't know if my issue has been dealt with somewhere in the forum or not (just too many treads to search... :( sorry).

My problem is that I have a new Dell Laptop with 2 HDD (320GB each). The primary drive has Vista installed and I want to have two more OS on the second disk. I would like to install Suse 11.1 and Ubuntu 8.10. I am able to install only 2 OS at a time. I can install successfully Vista & Suse or Vista & Ubuntu and not the three together. This is what I have done:

- I didn't touch the first Hard Drive with Vista
- I successfully installed Suse on the second one on a partition (I have partitioned the drive with Suse 140 GB and 10 GB for Swap)
- I am left with 150 GB free. I am trying to install Ubuntu on it with an ISO file, but it keeps failing on 54-55% of copying files. It says Error......CD/DVD problems or Hard Drive problem, please clean your CD....I know for definite that there's nothing wrong with CD/DVD or Hard Drive because if I reformat the entire disk with that Ubuntu CD and try to install Ubuntu alone, it installs fine.

Could anyone please help. I don't know if it's something to do with the boot loader, or I am not allocating correctly the swap for Ubuntu. Because I selected **ext2 **with **no swap** (and at this stage i cannot partition anymore the HD from the Ubuntu CD menu). On the boot loader issue, i don't know if it's something to do with the selection i am making on the last stage **(hd0)**.

Thanks for your help!

----------
Roi des Belges

---

### Post by Roi des Belges on 2009-03-10
Hi there! 

Is there anyone willing to help about my issue, or even give me the correct direction on the thread to use? Please?

Thanks!

> **Roi des Belges said:**
> Hi all,

I kinda have a rather different issue to this. I don't know if my issue has been dealt with somewhere in the forum or not (just too many treads to search... :( sorry).

My problem is that I have a new Dell Laptop with 2 HDD (320GB each). The primary drive has Vista installed and I want to have two more OS on the second disk. I would like to install Suse 11.1 and Ubuntu 8.10. I am able to install only 2 OS at a time. I can install successfully Vista & Suse or Vista & Ubuntu and not the three together. This is what I have done:

- I didn't touch the first Hard Drive with Vista
- I successfully installed Suse on the second one on a partition (I have partitioned the drive with Suse 140 GB and 10 GB for Swap)
- I am left with 150 GB free. I am trying to install Ubuntu on it with an ISO file, but it keeps failing on 54-55% of copying files. It says Error......CD/DVD problems or Hard Drive problem, please clean your CD....I know for definite that there's nothing wrong with CD/DVD or Hard Drive because if I reformat the entire disk with that Ubuntu CD and try to install Ubuntu alone, it installs fine.

Could anyone please help. I don't know if it's something to do with the boot loader, or I am not allocating correctly the swap for Ubuntu. Because I selected **ext2 **with **no swap** (and at this stage i cannot partition anymore the HD from the Ubuntu CD menu). On the boot loader issue, i don't know if it's something to do with the selection i am making on the last stage **(hd0)**.

Thanks for your help!

----------
Roi des Belges

---

### Post by pmurberg on 2009-03-15
I purchased a Dell XPS 435 MT with Vista SP1 and after 3 weeks of forum reading, I have not peeled installation issues to the center of the onion.

Does anyone have this worked out? Is there a how to somewhere?

---

### Post by munishvit on 2009-03-15
Sorry to mix-up my problem with this thread, but I too have problem with dual-boot and I want to install Windows XP on non-first primary partition. Please Check
[http://ubuntuforums.org/showthread.php?t=1095893](http://ubuntuforums.org/showthread.php?t=1095893)
aaanny help would be great. Thanks :D

---

