---
title: "Cannot mount external hard drive in Ubuntu"
date: 2009-06-05
forum: Hardware
---

### Post by ubbitz on 2009-06-05
Hello, I am very new to linux and I'm kinda an idiot when it comes to working with linux

I have a 1.5 TB external hard drive connected to my computer via firewire. It shows that it's connected, but when I click on it it says: "Cannot mount volume" and then the details to the problem read: 
'ntfs_mst_post_read_fixup: Invalid argument Index buffer (VCN 0x0) of directory inode 0x5 has size (24) differing from the directory specified size (4096). FAiled to mount '/dev/sdc1': Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc10. Please see the 'dmraid' documentation for more details.

PLEASE HELP!

---

### Post by Steelmourne on 2009-06-05
I've had a usb drive that wouldn't mount on Ubuntu. When I plugged it into Windows I was offered to scan it for errors which it fixed. It seems that there is something wrong with that filesystem on that drive.

---

### Post by healingmanos on 2009-06-05
Sorry I cannot help with your drive non-recognition, but would like to say I have had the same problem and am a novice to Ubuntu too. I am so pleased with Ubuntu but nevertheless the learning curve is steeply uphill at present and I daren't use the dos type application to install drivers etc in case I get it wrong. I do however recommend using other people's comments in the forums like this one. Did you get to resolve your issues? I am keen to share any new information I get from searches. For instance if you go to USB DRIVERS for Ubuntu in Google Search it gives you a very good explanation of how to open the terminal window and do it manually. Good luck.

---

### Post by ZeldeR on 2009-06-05
I'm not sure but I think you need ntfs driver support, or you must change the file system of the HDD to fat :roll:

---

### Post by HavocXphere on 2009-06-05
> **ZeldeR said:**
> I'm not sure but I think you need ntfs driver support, or you must change the file system of the HDD to fat :roll:
No. NTFS works just fine under ubuntu. I think the driver is part of the "restricted" package that pretty much everyone installs. I never specifically installed something called ntfs driver.

> Invalid argument Index buffer (VCN 0x0) of directory inode 0x5 has size (24) differing from the directory specified size (4096)
The filesystem is damaged so ubuntu is refusing to touch it.

You could probably force it to mount anyway, but it would be better to fix the problem. I'd try running Scandisk /chkdisk from a windows machine.

It is *possible* that the disk itself is damaged. However, chances are that the filesystem just got mangled when you pulled out the external drive without Safely Removing it/PC restarted etc.

---

### Post by ubbitz on 2009-06-05
thank you everyone for your help, i appreciate it.

right now i am downloading xp student and virtual box and im gonna try to run chkdsk with that.

if that doesnt work then i will just install windows on a partition and do that

and i am sure that the file system got screwed up because i never used the "Safely Remove" feature in windows

thank you

---

### Post by HavocXphere on 2009-06-05
> **ubbitz said:**
> right now i am downloading xp student and virtual box and im gonna try to run chkdsk with that.
The OSE version does not support all USB devices, so you might run into trouble there. The version from the website should work though.

> **ubbitz said:**
> and i am sure that the file system got screwed up because i never used the "Safely Remove" feature in windows
Lesson learned I hope. You can kinda do that with FAT formatted things but not ntfs.

---

### Post by ubbitz on 2009-06-05
> **HavocXphere said:**
> The OSE version does not support all USB devices, so you might run into trouble there. The version from the website should work though.


Lesson learned I hope. You can kinda do that with FAT formatted things but not ntfs.


what do you mean OSE version and what website?

(sorry i am very new to linux)

---

