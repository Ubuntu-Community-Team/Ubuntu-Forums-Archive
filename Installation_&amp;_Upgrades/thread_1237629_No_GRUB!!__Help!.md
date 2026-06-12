---
title: "No GRUB!!  Help!"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by vze4p6c2 on 2009-08-11
hi all,

I wanted to dual boot with WinXP so i installed ubuntu 9.04 and everything went well.  When the booting goes, I don't see anything that lets me choose the OS.  I don't think my bios sees grub or anything.  it just goes into win XP.  
A

Any suggestions are apprecitated.

thX!!!

---

### Post by ZaHACKieL on 2009-08-11
I guess you first installed Ubuntu and then XP right?

---

### Post by vze4p6c2 on 2009-08-11
no, xp was first.  I have three HDs.  Maybe that somehow messes it up?  Maybe grub was installed in a wrong HD?  thanks for ur reply'

---

### Post by ZaHACKieL on 2009-08-11
Ok, then, how did you install the Win and the Ubuntu? The Win in one HD and the Ubuntu in another HD?

---

### Post by vze4p6c2 on 2009-08-11
Uhh... I don't quite know.  When I go to Right Click on my computer and go to Manage > Disk Managment, i see that Boot is on a D drive and System of XP is on the C drive.  And ubuntu is on the D drive with swap.

PIC: [http://i719.photobucket.com/albums/ww193/vladtess/knkjn.jpg](http://i719.photobucket.com/albums/ww193/vladtess/knkjn.jpg)
55 Gigs is the linux partition and 2GB is the swap.

---

### Post by ZaHACKieL on 2009-08-11
I think what you should do is this: Install Windows in one HD, then install Ubuntu in another HD and leave the third HD as a shared HD.

If you have problems making a dual boot in separate HD, take a look here:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Let me know what happens

---

### Post by ZaHACKieL on 2009-08-11
> **vze4p6c2 said:**
> Uhh... I don't quite know.  When I go to Right Click on my computer and go to Manage > Disk Managment, i see that Boot is on a D drive and System of XP is on the C drive.  And ubuntu is on the D drive with swap.


I see...I think you need to have your C disk as the bootable and have the GRUB in your MBR.

If you want to use your second HD for Ubuntu, you should have it as ext3.

Take a look at the link I posted in the message before

---

### Post by merlinus on 2009-08-11
Are you using wubi, or separate partitions for ubuntu?

---

