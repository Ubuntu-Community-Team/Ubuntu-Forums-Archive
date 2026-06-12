---
title: "Installation Failed but Partitioning Successful... How to Proceed?"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by hopeididgood on 2009-04-30
I'm hoping to dual-boot my computer with Windows and Ubuntu.  I attempted to install Ubuntu 8.04. by CD and received an error message regarding my cd drive and a notification that the installation had failed.  I then attempted to install via USBdrive, only to discover that the partitioning had been successful.  

My issue is this... The Guided Resize wants to divide the space previously saved for Ubuntu again.  (So I'd end up with one Windows partition, and two separate -- one failed -- Ubuntu partitions.)  The Guided - Entire Disk option obviously, wants to wipe out all partitions, including my Windows.  

Which leaves me with the Manual option and a little unsure how to proceed.  

I like the file sizes that the original attempt with the Guided Resize set-up.  But how do I tell the installer exactly which part I want it on?  (And can I avoid it setting up additional swap parition?) 

I think my course of action is to double click the partition I want to install Ubuntu to (which I've recognized by the size) leave the size as is, set the Use As: to Ext3 journaling file system, tick the Format box, then select the / as the Mount Point...  And then leave all the other partitions alone... 

Can someone tell me if this is correct?  I'd be ever-so grateful for any advice!

---

### Post by Pumalite on 2009-04-30
XP or Vista?

---

### Post by hopeididgood on 2009-04-30
Xp.

---

### Post by Pumalite on 2009-05-02
Get Gparted Live CD, boot from it. Delete everything except XP (ntfs), format the new large space ext3. Install Ubuntu, go Manual and pick the new partition, give it a mount point '/'. Let Grub install by default. You'll have a brand new Grub and dual boot.

---

### Post by caljohnsmith on 2009-05-02
> **hopeididgood said:**
> 
I think my course of action is to double click the partition I want to install Ubuntu to (which I've recognized by the size) leave the size as is, set the Use As: to Ext3 journaling file system, tick the Format box, then select the / as the Mount Point...  And then leave all the other partitions alone... 

Can someone tell me if this is correct?  I'd be ever-so grateful for any advice!
Yes, that should work just fine. Let us know if you run into any problems.

Cheers,
John

---

### Post by hopeididgood on 2009-05-02
> **caljohnsmith said:**
> Yes, that should work just fine. Let us know if you run into any problems.

Cheers,
John


Thank you!  I gave it a try and it all seems to be working.  I'm enjoying my Ubuntu experience thus far!

---

### Post by caljohnsmith on 2009-05-02
> **hopeididgood said:**
> Thank you!  I gave it a try and it all seems to be working.  I'm enjoying my Ubuntu experience thus far!
Glad to hear that worked OK. Hope everything else goes as smoothly as possible with your Ubuntu experience, but if not, you know where to find us. :)

John

---

