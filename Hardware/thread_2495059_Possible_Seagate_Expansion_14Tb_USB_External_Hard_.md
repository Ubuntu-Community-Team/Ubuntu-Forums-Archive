---
title: "Possible Seagate Expansion 14Tb USB External Hard Drive Incompatibility with 23.10.1"
date: 2024-02-06
forum: Hardware
---

### Post by chaosjs0010 on 2024-02-06
Hello to all, Just wondering if my Seagate Expansion 14TB USB External Hard Drive is possibly incompatible with Ubuntu 23.10.1??  If so Then that would explain why I have a problem with gparted software on linux with this drive..  If not Then the question is there any possible way that I have not tried yet to fix this error : MFT Record 3 warning with input output error when mounting although I can mount it regardless now as it just forces the mount regardless most of the time!  Anyways Thanks for listening and Have a great day ahead and stay safe also!.

---

### Post by MAFoElffen on 2024-02-06
Incompatibilities? Not that I have heard, nor that others have reported. At least not with the drive and controller.

What is the partition table type, partitions and the formatted filesystem "type"?

The only time I hear of that error, coming back as an MFT Error: That has to do with a problem with the integrity of an NTFS filesystem, that may contain errors and needs to have 'CHKDSK' run on it from a Windows Machine to repair the filesystem. Linux can do it with 'fsck' though , but Windows deals with their own native filesystems better. Linux systems deal with ext4 and other Linux native filesystems better. fsck.ntfs & ntfsfix are a bit limited compared to chkdsk, when working with NTFS.

If you use this external drive just for Linux, you might think about reformatting it to Ext4. Would be faster, have a journal for better chance at data recovery and integrity.

---

### Post by chaosjs0010 on 2024-02-06
Hey there, The Partition Table Type is GPT I do believe and the formatted partition type is NTFS..  Yes I do mainly use it with Windows based system.  Thanks and Have a great day ahead also.

---

### Post by SeijiSensei on 2024-02-06
I have a 14 TB Seagate external connected via USB 3.0. I formatted it as a single ext4 volume with fdisk and mkfs. Never a glitch.

---

### Post by oldfred on 2024-02-06
Windows issue?
May be hibernated or fast start up is on which sets hibernation flag.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)

---

### Post by chaosjs0010 on 2024-02-08
Well There is something else that I noticed just today and everytime I reformat the drive and then format to NTFS filesystem via Ubuntu 23.10.1 linux and then the problem will go away only temporarily mainly because every single time I copy some files to the external hdd via Ubuntu 23.10.1 Linux OS, Afterwards it gives me this warning : Forced to continue.$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.  and etc..  On Windows 10 PE live iso of any sort I transfer files from there from hdd to external hdd it will be fine only until I boot into Ubuntu 23.10.1 Linux OS again!!..  So, Any ideas on this maybe??

---

### Post by yancek on 2024-02-09
The message you posted about the ntfs being inconsistent is usually associated with hibernation being on in windows when you are using that drive on windows.  When you mount it on a Linux OS, this is seen and it doesn't mount the filesystem due to high possibility of data loss.  The default with windows is to leave hibernation on and even if a user turns it off, some windows updates will turn it on again and of course, will neither ask or inform the user this is being done.

Have you run chkdsk from windows as suggested?  Much better to use windows tools on the proprietary windows fs..

---

### Post by chaosjs0010 on 2024-02-09
Yes and it will eventually come back right after I do more file transferring also!!..

---

### Post by MAFoElffen on 2024-02-10
Welcome to Ubuntu Forums.

Answer to your last post: "No. You are mistaken."

I tried to tell you in Post #2. It is now Post #9. You are not understanding what was said by anyone here: So let me spell it out.

Do you have Windows on a Dual-boot? If so, then a setting in Windows is causing this problem. Do not try to blame Ubuntu or Linux for a problem being cause outside it's control. It is not a problem with neither. That is just the facts. oldfred also tried to explain this to ytou and you blew him off, because you thought you knew better.

Go to Windows Control Panel > Power Settings > Action of Power Switch > Change the action from "Hibernation" to "Off". Done. That will fix that. Verify that you have done that.

If you do not have Windows as Dual boot, then there is not reason to have that drive formatted as NTFS. None at all. Then just format it is as EXT4 and be done with it.

If you do have Windows and are using NTFS as a go between filesystem between the two, then allow the framework for that to happen successfully. My niche as an IT consultant, is to tell people how to make Windows, Unix and Linux live together as one. People pay me for that advise. Here I do it for free.

Windows Hibernation is risky even for just Windows alone. It leaves the filesystem open on a power-off. I use Linux utilities to rescue Windows. I have Windows customers I support. They pay me well. I tell them if they have that setting "set to hibernate", I cannot support recover their filesystems if it crashes. Big Period. End of story. (Hear that.)

Listen to what others are trying to tell you here. If you do not understand what they are saying, please ask.

---

### Post by chaosjs0010 on 2024-02-11
Hello there, Well Truth be told My Windows based computer that I normally use the external hdd in question is back up and running now so Thanks anyways though..  Anyways, No problems now though to my knowledge anyways!  Thanks for trying anyways as well!  I really do appreciate it very much regardless.  Have a great day ahead and stay safe too as well!..

---

