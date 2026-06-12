---
title: "How to downgrade to the kernel?"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by iKevin on 2009-02-21
Hi All

I have installed intrepid on a machine with the D945GCLF motherboard.  All went well until ubuntu went through it first update.  After that point, there is now working network.  I used another machine and, through googling, discovered that there is a bug in the newer kernel for the realtek module for my network card.  

My question is this, Is there a way to install the kernel, and its dependencies, that is on the install CD for intrepid?  That kernel worked fine.

Thanks
Kevin

---

### Post by iKevin on 2009-02-21
Hi Again

Apparently, this bug has been fixed.  

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/326891](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/326891)

Is there a way for me to know that the next update has this particular fix in it?

---

### Post by iKevin on 2009-02-23
Ok, I think I made a fundamental mistake.  The kernel update is still buggy and it will apparently be fixed in the next kernel.  

My misunderstanding lies in the fact that I think the original kernel was still installed and I don't need to downgrade.  On a ubuntu only system, grub doesn't display a boot menu unless you hits ESC.   I just assumed that the old kernel was not available since there was "apparently" no choice to select it.  

I had reinstalled ubuntu and didn't let the kernel update.  I am going to update and press ESC to get the menu and confirm that I can boot from the previous good kernel.

Thanks

---

