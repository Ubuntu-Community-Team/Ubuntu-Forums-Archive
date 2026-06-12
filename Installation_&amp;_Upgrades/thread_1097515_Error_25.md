---
title: "Error 25"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Rilenator on 2009-03-16
Hi.

I recently downloaded the desktop ISO for Kubuntu (I cant remember which version but I'm pretty sure it was the latest one) and I wanted to install it to my extra HD. I had just formatted it (although it was in NTFS) so there was nothing on there. The installation went normally, but then when it restarts, while its booting up it comes up with this message:

"GRUB loading Stage 1.5

loading grub
grub error 25"

It comes up with this even when I'm trying to boot up from the other HDD (The one with Windows on it) So I cant open either of them. The only reason I can even go on here now is because I'm using the test version in the LiveCD.

At this point I don't even *want* to run Kubuntu....or any other distro...I just want my computer to be back to the way it was this morning BEFORE I installed it. I can still go into the folders with Dolphin, and my files are all still there (although for some reason there are a whole bunch of new files and folders in my C: drive that I've never seen before)
If I could just get back into windows I would be okay.....

+10000 internets to anyone who can help me:D

Thanks

EDIT: I meant to say Windows XP when I said Windows...

---

### Post by lindsay7 on 2009-03-16
If you are running windows vista, put your windows install disk in and boot it.  Get to the dos terminal or what ever it is called in windows, and run fix mbr.  You can find instructions on the web and I will also look for the bookmark that I have on this and post to you again.  Sorry I do not have the details off the top of my head. By the way, I think xp has a similar fix for what you need. The problem is that you need to restore you master boot record.

---

### Post by Rilenator on 2009-03-16
> **lindsay7 said:**
> If you are running windows vista, put your windows install disk in and boot it.  Get to the dos terminal or what ever it is called in windows, and run fix mbr.  You can find instructions on the web and I will also look for the bookmark that I have on this and post to you again.  Sorry I do not have the details off the top of my head. By the way, I think xp has a similar fix for what you need. The problem is that you need to restore you master boot record.

But won't that wipe all my data? D :

---

### Post by lindsay7 on 2009-03-16
No, it will not hurt anything on your windows system, it will just restore your original boot up to the way it was.

Here is the ms site and info.

[http://support.microsoft.com/kb/927392/](http://support.microsoft.com/kb/927392/)

---

### Post by Rilenator on 2009-03-16
Do you know if that will work in XP as well or is it specific to vista?

---

### Post by lindsay7 on 2009-03-16
Once you get back into window you can decide what you want to do. You can probable fix the boot up process to get both Kubuntu and windows to dual boot or you can try the install process again.  I do not what caused the problem but it sounds like a grub file problem (that controls the start up options for both Kubuntu and Windows once Kubuntu is installed). At any rate once you can boot to windows you can decide what you want to do.

I am new to Ubuntu too. I tried Kubuntu but I found it a little harder to work with for a first time Linux user. I might suggest that you install Ubuntu under Windows to give it a good try and see how you like it. Installed under window you can uninstall it from the add/remove programs in windows with no harm no foul.  Go to the "Wubi" web site for info and installation. It will install all by itself(you do not need to download the iso file.

By the way I really like Ubuntu and have enjoyed having it on my computer.

---

### Post by lindsay7 on 2009-03-16
The link I gave you is for Vista. XP has a similar fix. Here is some info from ms on xp. You may have to look around there site for all the details.

[http://support.microsoft.com/kb/321626](http://support.microsoft.com/kb/321626)

---

### Post by lindsay7 on 2009-03-16
Here is more info.

[http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/)

---

### Post by Rilenator on 2009-03-16
Okay thanks, I'll definitely try that.

---

