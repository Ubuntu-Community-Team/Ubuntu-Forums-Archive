---
title: "partial upgrade does not work in Jaunty"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by m4lte on 2009-04-30
**SOLVED**

I recently upgraded to Jaunty. It seems like everything works, my machine is running fine.
However, when I start the Update Manager, I get a message saying "Not all updates can be installed
Run a partial upgrade, to install as many updates as possible."
I click on 'partial upgrade' and a window title "Distribution Upgrade" saying it's "Running partial upgrade". Then I get a dialogue box saying "Do you want to start the upgrade.
1 package is going to be removed. 3 new packages ware going to be installed. 38 to be upgraded..."
I click OK, then the windows disappears and the Update Manager quits.

What could be the reason I can't install updates properly?


I have Jaunty 9.04, with Kernel 2.6.28-11 and GNOME 2.26.1 running on a ThinkPad R400.


**EDIT:**
I solved the problem running the Update Manager from the command line as described in this post: [http://ubuntuforums.org/showthread.php?t=1122008&page=2](http://ubuntuforums.org/showthread.php?t=1122008&page=2)
I got the partial upgrade installed and now everything seems to work again.

---

### Post by danebramaged on 2009-04-30
You are not alone in this.  I get pretty much the same thing.  (1 package is going to be removed.  3 new packages are going to be installed. 1 package is going to be upgraded.)  It wants to remove libdb4.5-java and, install libdb4.6-java, install libdb4.6-java-gcj, install liblrdf0 and Upgrade liblucene2-java.

I then click on "Start Upgrade" and I get nothing.  The window disappears and that is all.

I am upgrading from 8.10 TO 9.04 on an AMD Sempron 3100+


**UPDATE**:  Yep.  Works for me.

---

### Post by Pointu on 2009-04-30
Thank you for sharing this.  I had the same problem too and this solution worked for me too.

---

### Post by flarkit on 2009-04-30
Hi,

Another 'thanks' from me. Also solved this for me by running "sudo apt-get update && sudo apt-get dist-upgrade"
:)

---

### Post by spmccann on 2009-05-04
Thanks for that it was bugging me. Now just to fix xorg with the intel chipset and I'm sorted.

---

