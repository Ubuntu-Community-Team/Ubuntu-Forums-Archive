---
title: "HP Mini 210 Dual-Boot Ubuntu advice"
date: 2012-05-09
forum: Hardware
---

### Post by Raweed on 2012-05-09
Hi, I've just ordered my HP Mini 210 Netbook (250GB HDD & 1GB RAM - will upgrade to 2GB asap) and would like to like to dual-boot with ubuntu, It comes with windows 7 starter pre installed.
I have managed to get hold of the original partition table which are as follows:
209M use: Windows boot loader
211GB use: Windows 7
15G use: HP Recovery
108M use: HP Tools

Preferably I would like to keep the Recovery Partition as it does not have a CD drive so I cannot make a backup of it. I don't mind reducing the Windows partition but the obvious problem here is that I already have 4 Primary partitions, I am unsure of what HP_TOOLS partition is for but I would guess its to load the factory image in case of failure. Is there a way to use/convert into logical partitions or would that not help? Any suggestions welcome. Thanks in advance.

---

### Post by oldfred on 2012-05-09
The normal advice to to burn the HP recovery to DVDs so you can reinstall when the hard drive fails. How does HP suggest you do it?

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. fullcirclemagazine.org
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.

You can create Windows repairCD to a USB.

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Raweed on 2012-05-09
> **oldfred said:**
>  How does HP suggest you do it?
Thanks for the reply, I will email them as soon as my product arrives, and I cannot currently create a Recovery DVD as you and your links suggest as the laptop does not have a CD/DVD drive. In another link I have read that it is possible to copy the HP TOOLS partition onto an external drive, then completely delete the partition and create a new logical partition with the same name and paste the contents back in using a Ubuntu Live USB (i.e. mounting to logical HP TOOLS and pasting with the same hierarchy as before). Is this possible to do as this would allow me to add a another partition which I could install linux in. Thank you for your support.

---

### Post by oldfred on 2012-05-09
I think that is one of the suggestions. 

Some have made DVDs and erased both the HP tools & recovery as recovery has no use if drive dies. Some have said they never use HP tools. And at one post said that was easily downloaded, where a full recovery DVD may not be free.

Most also suggest that you houseclean cruft, do all your updates and then make a full backup, so you can easily restore without having to redo all that.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Raweed on 2012-05-09
Ahh okay I see, I'll just make images of the partitions and delete HP Tools and if needed Recovery. And after I have adjusted & deleted the partitions as appropriate it is a simple case of choosing the 'install alongside windows' option during installation right? or are there any other complications I should be aware of?

---

### Post by oldfred on 2012-05-09
You can just install alongside and it will create / & swap. But I usually suggest a shared NTFS partition, so you do not write into the Windows system partition. Windows has been known to have issues with too much activity from another system.

Another issue is whether system is old style BIOS & MBR (even if UEFI capable) or UEFI and gpt. Most new systems are UEFI, but not many are booting with UEFI from vendors yet.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:

Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

