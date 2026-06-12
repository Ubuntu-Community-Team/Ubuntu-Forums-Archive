---
title: "Wubi install of Ubuntu, XP64bit, and Win 7"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by CompSciSTL on 2009-10-20
Hello,

I have a desktop that currently has XP 64-bit along with a Wubi installation of Ubuntu 8.04 64-bit (on the same drive).  I was going to add Windows 7 64-bit to a separate HD on the computer.  Do you think it would be less of a hassle to uninstall the Wubi installation and to do a new Wubi installation of the latest version of Ubuntu, or could I leave everything as is and just install Windows 7 on the new HD?

Thanks!

---

### Post by stlsaint on 2009-10-20
im not sure where your question is...do you want wubi on the win7 hdd? from what i get all will be well as you are not touching your 64bit xp. if i didnt answer your question please rephrase.

---

### Post by CompSciSTL on 2009-10-20
Let me rephrase the question...

If I leave the my current setup as is and attempt to Install Windows 7 on the separate hard drive, will the Windows bootloader and GRUB conflict with each other?  

If they will conflict, would it be an easy fix, or would it be less hassle just to un-install my current Wubi installation and to just re-install after Windows 7?

Hopefully this clarifies my question.

---

### Post by Mark Phelps on 2009-10-21
> **CompSciSTL said:**
> If I leave the my current setup as is and attempt to Install Windows 7 on the separate hard drive, will the Windows bootloader and GRUB conflict with each other? 

No, they will not conflict but if all the drives are connected when you install 7, it will overwrite the MBR of your boot drive.  MS Windows installs always do that by default.

>  If they will conflict, would it be an easy fix, or would it be less hassle just to un-install my current Wubi installation and to just re-install after Windows 7?

After 7 install, just insert a LiveCD and use it to reinstall GRUB.  If should find the 7 installation as well and add a stanza for that.  But be aware that 7 will most probably write its loader files to your XP 64-bit partition, so when you get an MS OS selection menu, it will show both XP and 7.  GRUB will not allow you to select either OS by itself -- you will always get the MS OS selection menu after that.

---

### Post by raprap30 on 2009-10-21
If you want to use GRUB, follow the directions the guy above said, and if you want to use windows bootloader (which win7 will use), your Wubi should stay.

---

### Post by CompSciSTL on 2009-10-22
> **Mark Phelps said:**
> No, they will not conflict but if all the drives are connected when you install 7, it will overwrite the MBR of your boot drive.  MS Windows installs always do that by default.



After 7 install, just insert a LiveCD and use it to reinstall GRUB.  If should find the 7 installation as well and add a stanza for that.  But be aware that 7 will most probably write its loader files to your XP 64-bit partition, so when you get an MS OS selection menu, it will show both XP and 7.  GRUB will not allow you to select either OS by itself -- you will always get the MS OS selection menu after that.


If I disconnect my XP64/Wubi drive, perform the install on the blank drive, and reconnect the XP64/Wubi drive, would I still need the live CD, or could I manually edit the Boot file from my current installation?

---

### Post by Mark Phelps on 2009-10-23
> **CompSciSTL said:**
> If I disconnect my XP64/Wubi drive, perform the install on the blank drive, and reconnect the XP64/Wubi drive, would I still need the live CD, or could I manually edit the Boot file from my current installation?

You would need GRUB installed to the MBR of whichever disk your booting from.  Unless GRUB is already there, you would need to boot from the LiveCD to install it there.

If all disks are connected when you reinstall GRUB, it should find all the OSs and automatically add stanzas for them, so most likely, you would not have to manually edit the menu.lst file.

---

### Post by CompSciSTL on 2009-10-24
I wonder if I have hosed things up a bit...

Here is what has happened so far:

I left my existing XP64/Wubi drive untouched and installed Win7 on the blank drive.  After installation, I noticed that I wasn't getting any boot selection menu, from GRUB or Windows.  I was booting straight to Windows 7.

I tried the instructions in this link to at least restore XP64 as a boot option.  [http://www.kombitz.com/2009/01/13/how-to-add-windows-xp-to-windows-7-boot-manager/](http://www.kombitz.com/2009/01/13/how-to-add-windows-xp-to-windows-7-boot-manager/)  All that did was create a Windows XP menu option in the Windows Bootloader, but it wasn't able to boot to XP64 bit.

Next, I tried this option to try and restore GRUB:  [http://paranoid-engineering.blogspot.com/2008/12/how-to-restore-grub-after-windows.html](http://paranoid-engineering.blogspot.com/2008/12/how-to-restore-grub-after-windows.html)  
When I tried the find command mentioned in that link, I received an Error 15:  File not found message.

During continued searching, I discovered this link recovering GRUB:  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Should I go with the section entitled "Overwriting the Windows Bootloader", or maybe using that Super Grub Disk mentioned about halfway down the page, or is there a third option that is more appropriate for my situation?

---

### Post by CompSciSTL on 2009-10-24
Here is a new update:

Just to see what would happen, I went into the BIOS and changed the boot order of my Hard drives so that the XP64/Wubi would boot first.  I proceeded with booting and Windows XP64 (and Ubuntu on a separate reboot) booted like nothing actually happened!  It appears that Windows 7 didn't even touch the MBR of the other drive which is really strange.  Should I go ahead with an edit of the menu.lst file to add Windows 7 to the list?

:confused:

---

### Post by forkxxrbhi on 2009-10-24
they will not conflict

---

### Post by Mark Phelps on 2009-10-26
> **CompSciSTL said:**
> ... Should I go ahead with an edit of the menu.lst file to add Windows 7 to the list?

If Windows 7 detects another MS Windows OS in the system when it installs, it often installs its boot loader files to the partition for the other system.   So, if you already have a menu.lst entry for XP 64-bit, it might already work with Windows 7.

If not, go ahead an add another stanza for Windows 7.

---

