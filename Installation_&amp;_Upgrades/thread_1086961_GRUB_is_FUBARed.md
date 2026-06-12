---
title: "GRUB is FUBARed"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by Zaragon on 2009-03-04
I just attempted to set up a dual-boot Vista/Ubuntu system.  Vista already present on C:.  Installed Ubuntu with no discernable errors on another HDD.  Upon restart, I got GRUB error #22.  I had to do a bunch of /fixmbr things to get Vista back.  Now have computer booting straight into Vista as before.

What is error 22 and do I have to re-install Ubuntu or will EasyBCD find it?  Or, has anyone got any more valid suggestions?

Thanks, Zack

---

### Post by 73ckn797 on 2009-03-04
Maybe you could download "Super Grub Disk" and boot from that CD. Have it fix the problem for you. There are other ways from the Ubuntu Live CD but you will have to look around the forums for that answer. I have not had to mess with that.

I think this link should answer your question. [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) 

What you need to know is near the bottom of the page. The Community Documentation will be a great source for most questions you will have.

---

### Post by ASchweitzer on 2009-03-04
Well, GRUB error 22 indicates that GRUB can't find the partition it's installed on, which usually happens when the Ubuntu partition is deleted. Run a live CD to make sure your partition is still around, and then check here for threads on error 22. You can use the live CD to restore GRUB, but you'll have to ad Vista manually to the menu. The easiest solution is probably to reinstall Ubuntu, if you have no data to save.

---

