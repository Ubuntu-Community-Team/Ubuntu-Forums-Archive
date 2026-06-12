---
title: "Unable to Mount Location - Forcing a Windows Drive to be recognised and accessed."
date: 2011-02-08
forum: Hardware
---

### Post by cobba1982 on 2011-02-08
Hi all,

I have a Dell 1555 with Windows 7 installled. A week ago I got the dreaded 'Unmountable Boot Sector' warning and now the computer is unusable. I cant load into Windows, I cant enter through safemode or even repair.
So I was advised to try Ubuntu to recover my precious data, my university work and family photographs.

I read an article which said I could somehow force my Windows hard drive to be recognised or mounted in Ubuntu and I could then gain entry to it and copy my precious data onto a USB drive. 

My drive shows up on Ubuntu as '500 GB  Hard Disk: OS' and when I click on it, it says:

"Unable to mount location
DBus error.org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remove application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken"

I have entered the APPLICATIONS / ACCESSORIES / TERMINAL
This is where I am stuck. Does anyone know the next steps in forcing my harddrive to be recognised and accessed. I believe my hard drive is FAT32. 

So I need your help. Could anyone please give me some advice about how to go about this. Any help or advice would be greatly appreciated and I would be eternally greatful! :-)

P.S I can post screenshots along the way if needed

Rob - New Zealand

---

### Post by cobba1982 on 2011-02-08
Upon clicking on the drive just now it came up

"Unable to mount location
Error mounting: mount exited with exit code 13: nfts_attr_pread_i:nfts_pread failed: input/output error Failed to read NTFS $Bitmap: Input/Output error NTFS is either inconsistent or there is a hardware fault, or its a SoftRAID/FakeRAID hardwaer. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/directory, (e.g /dev/mapper/nvidea_eahaabcc1). Please see the 'dmraid' documentation for more details.

I am having a bit of difficulty understanding all of this. Thanks again in advance

Rob

---

### Post by cjhabs on 2011-02-08
Rob

I know this is an Ubuntu forum, but when I have this type of problem, if I can't access the data from Ubuntu I try a different approach. Sometimes the disk needs to have chkdsk run to clear it before being able to access it. I remove the drive and connect it externally via a SATA/IDE to USB adaptor to a Windows box and then run chkdsk on it. If that works I can grab the data from windows or go back to Ubuntu again.

Good luck

---

### Post by cobba1982 on 2011-02-08
Thanks for your reply. I have tried to attach it via a USB mount to a few other windows computers but it hangs the computers as soon as the drive is recognised in 'my computer'. I cant get to the point where it will allow me to run a chkdsk
Is there any way to force the drive to be recognised in Ubuntu? That might be my only way in to the disk to recover the files.
Thanks so much I look forward to your advice

Rob

---

### Post by oldfred on 2011-02-08
To confirm if it is NTFS or FAT. This may show partition.

```
sudo fdisk -lu
```


Ubuntu & gparted will not normally mount a NTFS partition that has the chkdsk flag set, to prevent further damage that chkdsk then may not be able to repair.

I would try chkdsk from a windows repairCd. 

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

You can use any of these to run chkdsk on NTFS.
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

You can try ntfsfix from Ubuntu with the ntfs tools. But it will leave the chkdsk flag set. Also shows the force command in the example error box.
[http://mpathirage.com/how-to-fix-ntfs-mount-error-on-ubuntu/](http://mpathirage.com/how-to-fix-ntfs-mount-error-on-ubuntu/)

---

