---
title: "Delete Ubuntu Partion (9.03) to reinstall Ubuntu (8.10) ?"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by Maximilian Maksutovic on 2009-04-14
Hello everyone, 

I had successfully created a Dual Boot with Windows XP and Ubuntu 9.03. Unfortunately through inexperience and meddling with KDE and Kubuntu (and doing a poor job of installing ATI video drivers ((made errors to /etc/X11/xorg.conf -- and even with re-edits using nano in root command and dpkg-reconfigure -phigh xserver-xorg, i can not load a successful .conf file)-- i have made GNOME completely unstable and can only boot in root command with networking. I am looking to reinstall Linux, however I am wondering if Ubuntu 8.10 might be more stable (even though 9.03 is released in a few days?). My question concerns how I should handle the reinstall. I am assuming i can do this by booting my CD and in Step 4 (of 7) "**Prepare disk space**" I will select **Specify partions manually (advanced)**" -- in this window i see my windows partion set as "**/dev/sda1  type: NTFS** and my Ubunutu partion as "**/dev/sda5  Type: ext3**" (there is also a **/dev/sda6**  type swap... size at 4112 MB, but using none. Also there is a **/dev/sdb** with no other information....) Is it as simple as deleting the **/dev/sda5  type: ext3** partion, and reinstalling Ubuntu in the empty partion space? Or will I be in bad shape for either the new installation or my currently bootable windows XP? Also I would like to hear your opinion if I should try Ubuntu 8.10 as I am new to this extraordinary world of Linux. Thank you for your time

---

### Post by kjaada on 2009-04-14
You could do what you intend but I think you did miles too much tweeking on yr 1st install.Next time be content to try rather than change so much for a while.Also 9.03 was a progression towards 9.04 which is better and tweekd to near release stage.With daily updates to a point you would be letting the development team do the tweeking.

---

### Post by Maximilian Maksutovic on 2009-04-14
kjaada,

Thank you for your advice. I have been reading many commentaries on new users getting ahead of themselves, and I realize I am apart of them and apologize for the naive questions we must ask now. I am so appreciative of the tremendous support that these forums provide and strive to become apart of the support.

I just wanted to confirm that by deleting the **/dev/sda5 Type: ext3** that I will be able to reinstall Ubunutu * without * damaging my ability to boot into Windows. Also i wanted to comfirm that the two additional partitions of **/dev/sda6** type swap... size at 4112 MB(nothing written to it) and **/dev/sdb** *should* or [I]should not[\B] be deleted. 

Thank you again for your time.

---

### Post by cariboo on 2009-04-14
You don't have to delete any partitions, when doing a reinstall. When you get to the partitioning section, choose manual then select the partition and edit it, make sure to set the mount point and mark it for formatting.

Jim

---

### Post by kjaada on 2009-04-14
Do remember to tell us how you get on.

---

### Post by BlueCanary9999 on 2009-04-14
I'm not in exactly the same situation as Maximilian, but I want to reinstall Ubuntu 8.10.  I'm at the Edit Partition step following cariboo's advice.  But being completley new to Ubuntu, I'm not sure what to set the Mount point to.  My options are:
/
/boot
/home
/tmp
/usr
/var
/srv
/opt
/usr/local
Which am I supposed to pick?

Also, for the "Use as" drop-down box, I pick "Ext3 journaling file system," right?

Sorry for the newbiness.  And thanks in advance.

---

### Post by kjaada on 2009-04-14
Use / which means root
 And yes EXT 3 is the one

---

### Post by BlueCanary9999 on 2009-04-14
Ah, thank you so much!

---

