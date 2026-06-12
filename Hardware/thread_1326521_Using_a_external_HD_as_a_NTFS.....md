---
title: "Using a external HD as a NTFS?...."
date: 2009-11-14
forum: Hardware
---

### Post by VcDeveloper on 2009-11-14
I have an external drive previously formatted for Windows with a long file name as the label.  Example: "Corporate Web Server".  I would like to use the HD as my primary backup, but I concern it will not work because 1) the long name, and 2) it's a NTFS.

My question is, is it possible to change the label, because it was disabled in Disk Utility or what is the best way I can set this HD as my primary backup?

---

### Post by coffeecat on 2009-11-14
I believe the maximum label length for a NTFS partition is 32 characters, and "Corporate Web Server" is well within that. Since the ntfs-3g driver used in Ubuntu needs to work without issue with NTFS (obviously), it *ought* to be happy with a label name within that limit. Why not simply plug the drive in to Ubuntu and see what happens?

As far as it being NTFS, this should not be a problem, except for the proviso mentioned below. NTFS read/write is reliable in Jaunty/Karmic. Simply plug it in and it will be automounted. I have several external drives formatted NTFS and they work just fine with Jaunty and Karmic. (They worked just fine with Hardy and Intrepid.)

Next - to be able to label or relabel an NTFS partition in Ubuntu, you need to install the package ntfsprogs. This is present in the live CD environment (so you could relabel using the live CD if you wished) but not in a default hard drive installation. With ntfsprogs installed you can label a NTFS partition with "ntfslabel" from the terminal, or by using Gparted (you'll have to install Gparted first), or with Disk Utility. Or, if you have a Windows machine handy, you can relabel using that - it's quick and easy in Windows.

The caveat: NTFS is a Microsoft filesystem. The various utilities available in ntfsprogs are very good but not complete because the developers have had to reverse-engineer all the code. Microsoft is not exactly the epitome of openness. :rolleyes: A possible problem is that if you suffer a corruption to the journalling of an NTFS partition, you may need 'chkdsk' in Windows to repair it. The Linux tools may not be up to the job. So - if you do not have a Windows machine handy for this sort of eventuality, you might want to reconsider the filesystem you use on that external drive.

---

### Post by VcDeveloper on 2009-11-14
Ok Thanks! Looks like I will just plug it in my other Windows computer and change the label.  I appreciate your help!

---

