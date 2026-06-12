---
title: "Help, can't boot into Windows."
date: 2008-07-18
forum: General Help
---

### Post by rudedoggx on 2008-07-18
Hey, I've been dual-booting between Windows XP Media Center and Ubuntu using Wubi, but I recently ran into a problem.  I changed some settings in Windows so that Wubi is the default on the list of OS's you choose from at boot. I also unchecked the box that allows a timer, so it automatically boots into Ubuntu. From here, I thought I'd be able to boot into windows by pressing ESC when it says "Press 'ESC' to enter menu, but when I select Windows XP to boot, it says:

error occured while savedefault

Can anyone help, please?

---

### Post by nwubie on 2008-07-18
If you press c at grub's boot menu you'll access a command line prompt. I know some commands allow you to find a missing installation but can't tell you exactly which ones. Better wait for an expert or do some serious search before you try the commands there. Here's the list and some help : [http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html](http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html)



If the only changes you made in XP were some modifications in the boot.ini file (either via msconfig or via the system properties => advanced => settings under startup and recovery => change button) then I guess that restoring that file to its original state would solve the issue if the "wubi line" is still there. It'll be something like 
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Media Center Edition" /fastdetect /NoExecute=OptIn
wubi line

```
I can't tell you the exact content of the "wubi line" cause I'm not on my own computer right now. If no-one has replied until then I'll post back on sunday with the exact content.

Also note that the multi(0)disk(0)rdisk(0)partition(1) line may be different on your computer if XP is not installed on the first partition of the first physical drive.

If XP is on a separate partition you'll be able to mount it and edit the boot.ini file in Ubuntu. If wubi was installed on the same partition as XP it can be tricky. I for myself was able to mount all NTFS partitions in Ubuntu except the one that holds the Ubuntu image/wubi installation.

Else you could take the hard drive out of the computer and hook it as slave in another computer to edit the boot.ini file there.

Keep in mind that the boot.ini file is an hidden system file so you'll have to allow Nautilus or Windows Explorer to see it before you can edit it. In Windows explorer it's tools => folder optiosn => view => tick "view hidden files and folders" and untick "hide protected operating system files". You'll also want to make sure that the file is not read only (right-click => properties in XP).



If you have the XP media center install CD you can also restore the original boot loader and boot.ini file using the recovery console. I have yet to try to access my windows installation from the recovery console after the boot loader had been replaced by grub. I'll give it a try once I'm back at my place (on sunday if you're willing to wait until then). This method will only work if grub's boot loader doesn't prevent the recovery console from accessing your windows installation. Once back in windows backup your wubi folder (or just the ubuntu image, which is the biggest file in the folder), reinstall wubi and copy back the backed up file(s). 

To restore XP's original boot loader and boot sectors : insert the XP CD, enter the BIOS at startup (repeteadly press del or look for some "press xx to enter setup" message) to change the boot order priority to CD-rom first and press enter to boot from the XP CD when prompted to. At the first installation screen press 'R' to access the recovery console. Select your windows installation and enter the admin password if prompted to (press enter if the password was left blank). At the c:\windows\ command prompt type
**fixmbr**
**fixboot**
**bootcfg /rebuild**
then follow [these instructions](http://support.microsoft.com/kb/330184) starting from step 8 (replace the load identifier by Windows XP Media Center Edition).

---

### Post by ago on 2008-07-21
From ubuntu you can edit boot.ini in C: (/host in Ubuntu) and change the default/timeount.

---

### Post by nwubie on 2008-07-23
@ rudedoggx : any luck getting back into Windows ? 

Fyi I just tried booting on the XP CD to enter the recovery console and had no problems doing so. But as ago said the easiest solution is to edit the boot.ini file from within Ubuntu.

The content of the last line related to wubi in the boot.ini file should be
c:\wubildr.mbr="Ubuntu"

> **ago said:**
>  C: (/host in Ubuntu)
So that's where the partition hosting the wubi image was hiding... :)

---

