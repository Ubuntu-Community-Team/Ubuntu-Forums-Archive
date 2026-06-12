---
title: "trouble with liloconfig after Jaunty upgrade"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by livtin on 2009-04-24
During upgrade from intrepid to Jaunty I recieved a message which informed that there was no previous version of Lilo and I should run liloconfig and then sbin/lil.  Unfortunately when I tried to run liloconfig I recieved the following message
WARNING!                                                                  &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Your /etc/fstab configuration file gives device                           &#9474; 
 &#9474; UUID=87279d44-51c1-486f-9288-029bb0538f54 as the root filesystem device.  &#9474; 
 &#9474; This doesn't look to me like an "ordinary" block device. Either your      &#9474; 
 &#9474; fstab is broken and you should fix it, or you are using hardware (such    &#9474; 
 &#9474; as a RAID array) which this simple configuration program does not         &#9474; 
 &#9474; handle.                                                                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; You should either repair the situation or hand-roll your own              &#9474; 
 &#9474; /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig  &#9474; 
 &#9474; again to retry the configuration process. Documentation for LILO can be   &#9474; 
 &#9474; found in /usr/share/doc/lilo/.       

How do I fix this please.  I am an absolute beginner so will need detailed direction.
Thanks:confused:

---

### Post by Dexx4d on 2009-05-09
I'm having the same problem.  My previous hard drive had failed and I've just installed a new 500gb seagate sata drive.  Used my old ibex live cd to install, then upgraded to jaunty.  First upgrade failed halfway, so I ran it again.  The second time I got a different dialogue that walked me through a  "partial upgrade".  About halfway through, I received a warning that I needed to run liloconfig and then /sbin/lilo when done or lilo wouldn't work.

When I run liloconfig, I get the a similar error to the original poster.

---

### Post by livtin on 2009-05-09
After a little digging and re-reading the installation notes I discovered that the Lilo thin is a known issue.  It seems Lilo is a boot loader which is not required in this distribution of Ubuntu asince the boot loader for Jaunty is grub and it is working just fine.  After I had watched the boot sequence to ensure that Grub was working correctly I made sure that Lilo was uninstalled and all is well!!
:P

---

### Post by Dexx4d on 2009-05-09
Thanks for the update!

---

