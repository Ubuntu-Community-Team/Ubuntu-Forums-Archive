---
title: "Partitioning best suited for XP dual booting."
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by raja_s_patil on 2009-03-31
Hi,

I am in process of Installing XP and Kubuntu on a new
machine with 250 GB HDD. We need about 25/30 GB For windows and rest will be KUbuntu. I would like to know what is best practice Partitioning so that reinstalling any OS in due course of time will not break other OS and there is minimum data loss. We need lot of space to store lot of data accessible from both the OS. This is a machine for my kids who make use of internet and I would like to make them
use Ubuntu for Internet access so that they are protected from any virus/malware attacks. However I know that viruses attached to files can infect windows when they are used there so they should be able to reinstall XP at any time without any data loss or stop unubtu from loading. At present i did 
straight royal dual booting but reinstalling stopped the ubuntu booting and I need to reinstall it again. So i would like to steps right now so that in future this sort of problem can be avoided

Thanks and Best regards

Raja

---

### Post by Partyboi2 on 2009-03-31
You could create a separate ntfs partition that both operating systems can read write too for storing you data, then if you have to reinstall either os the data will be untouched as its on its own ntfs partition. 
If you reinstall windows at any time you will need to restore grub to be able to boot back into ubuntu, this can be done using a ubuntu live cd. See [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351").

---

