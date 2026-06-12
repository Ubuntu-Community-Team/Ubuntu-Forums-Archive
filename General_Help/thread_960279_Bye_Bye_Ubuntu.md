---
title: "Bye Bye Ubuntu"
date: 2008-10-27
forum: General Help
---

### Post by iano.it on 2008-10-27
Hello,

Im looking some help in removing Ubuntu.  I used Wubi to install ubuntu in dual boot config with windows xp.  I sadly seriously messed up my Ubuntu by playing with things too much.  I would like to remove it.  Just to clarify is this process ok to follow even though I used Wubi.

Boot to the recovery console using your XP CDROM, enter the commands "fixboot" then "fixmbr" and reboot. XP should boot, GRUB will not load at all as it should have been removed from the bootloader.

Once XP has booted go to start -> run and enter "diskmgmt.msc". Look for the Linux partitions and delete and format them into NTFS or FAT32.

Thanks for your time in advance.


Ian

---

### Post by ago on 2008-10-27
There is no linux partition if you used wubi, just files. So deleting linux partitions is not going to help much. Same thing for fixmbr/fixboot as the mbr is not modified...

You can remove Wubi from the control panel > add/remove software, if you used wubi 505 see [https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu)

In the same guide you will find instructions for manual uninstallation if you prefer that.

---

### Post by iano.it on 2008-10-27
Thanks alot for that inforamtion.  Hopefully this will just work, then after its un-installed I can download and use the new Ubuntu (yay)

Thanks again.

---

### Post by ago on 2008-10-27
Go for 8.10 at this point.

---

### Post by NosLycn on 2008-10-27
WUBI uninstalls like any other program in Windows, at least it did for me.

---

### Post by Mason Whitaker on 2008-10-27
Yeah, you shouldn't have any troubles at all uninstalling Ubuntu.

Ubuntu runs off of Windows' own partition, so there really is no true Dual booting going on.

---

### Post by timbolina on 2008-10-27
Okay, about two months ago i installed Ubuntu 8.04 using Wubi in Windows Vista. Recently, when i've been using Vista i've been having problems (Vista programming problems - they've screwed something up which they seem unable to fix - not a virus problem though) 

So I've decided to go purely for Ubuntu - and get rid of Vista. But first of all, I've got a few questions.

[LIST=1]
[*]Firstly, do i have to uninstall ubuntu before making Ubuntu my sole OS
[*]Secondly, what would be the easiest way to transfer my vista files (i.e. music, documents) to ubuntu
[*]Thirdly, do you know which media player would be the best for an iPod - would it be Songbird?
[*]Finally, I presume i should upgrade ubuntu to 8.10
[/LIST]

Thanks in advance

Tim

---

