---
title: "Removed windows vista and installed windows 7; grub never sees the light of day"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by JamesBowen on 2009-05-28
I was told I could fix this by running update-grub from a live disk.  Unfortunately, that didn't do it for me.

What do I need to do to make it so that my default boot loader is grub, and grub is pointed to my new win7 partition?

---

### Post by lindsay7 on 2009-05-28
See if this works for you. Type these commands in the terminal





Sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hdx)
quit

---

### Post by dr_rimzi on 2009-08-26
I have the same situation, and tried these would - be solutions, but none worked:

The above manual commands,
The super grub disk auto-recovery.

My 2 disk setup follows:

disk 1 contains:

hda1 - my ntfs data drive. Windows 7 is not installed here, but I suspect it's bootloader is here.

disk 2 contains:
hdb1 - my Windows 7 ntfs main partition
hdb2 - my Ubuntu 9.04 ext3 partition
hdb3 - ubuntu's swap partition
hdb4 - my ntfs data drive. No OS boots from here.


I'm all lost here.. could you help me please? :confused:

--
Thanks!
RimZi

---

### Post by Mark Phelps on 2009-08-26
To find out which disk contains the Windows 7 loader files, just open each one in Places and look for the BOOT folder.  That's always written to the partition that boots Windows 7.

---

### Post by dr_rimzi on 2009-08-27
Thanks for your reply.

I solved my problem, by issuing these commands:

find /boot/grub/menu.lst
**(hd1,4)**
setup (hd1,4)
root**(hd0)** 

(hd0) because the MBR is on another disk! SGD didn't notice it, heh


Thought I just share my solution.. :popcorn:

--
RimZi

---

