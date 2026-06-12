---
title: "kickstart installation of Ubuntu"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by anirudha.sonar on 2009-06-18
Hi All,

I am bit new to ubuntu. I am trying to perform the kickstart installation of Ubuntu710-server, I have generated the ks.cfg file and have added all the necessary lines as per my requirement. After this I have edited the isolinux.cfg file and given the path of ks.cfg as below, 

====================================================
menu label ^Install Ubuntu 
      kernel /casper/vmlinuz 
      append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz ks=cdrom:ubuntu.ks.cfg quiet splash --
====================================================

But when ever I am trying to install the ubuntu from this CD , its not taking the direction for installation from ks.cfg file. Can anyone tell me what exactly I should add to isolinux.cfg/menu.cfg

I have perform the ks.cfg silent installation with RHEL and SLES it works perfect , but in case of Ubuntu dont have enough idea , so not able to debug where am i going wrong. 
Please guide me, and if possible please show me the isolinux.cfg/menu.cfg sample file with those entries.

---

