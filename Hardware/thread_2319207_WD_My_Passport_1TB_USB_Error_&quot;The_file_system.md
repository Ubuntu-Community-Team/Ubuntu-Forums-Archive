---
title: "WD My Passport 1TB USB Error: &quot;The file system wasn't safely closed on Windows...&quot;"
date: 2016-04-01
forum: Hardware
---

### Post by cyborgninja2 on 2016-04-01
Screenshot of error message is attached.

My WD Passport 1Tb external USB drive will not mount either in Ubuntu or Windows due to this error. Can anyone shed any light on what the problem is and any possible solutions?

What occurred: I plugged my WD Passport 1TB drive into my Xbox 360 via USB. The Xbox 360 notified me that formatting was necessary in order to use the drive on the console. I said, "Nope, no way, I'll pass. Thanks." and immediately unplugged the drive and powered off the xbox.

Now, the Passport USB drive will not mount properly on Ubuntu or Windows. The drive has power (drive light is lit and active) , platters are spinning AND the Passport HDD icon appears on the Ubuntu desktop and  likewise under My Computer via Windows. However, the drive contents are inaccessible when clicking to access the drive icon. The process of opening will 'hang' and freeze up.

Please see the following attached screenshot for the exact error message that pops-up (note that I blacked out my username):

[ATTACH=CONFIG]268127[/ATTACH]

I am assuming that in my haste, the drive was corrupted due to improper dismount from the Xbox console?? 

Google searches suggest that I run chkdsk /f or chkdsk /r on the drive via Windows. Upon running "chkdsk /f h:" (where "h:" is the passport drive letter) under Windows XP via CMD line, the process appears to run with no end in sight. I get literally thousands of lines of "file record segment unreadable" (followed by the drive segment number) and this appears to go on with no real end in sight. I cannot check % of completion b/c the terminal window is flooded with the "file record segment unreadable" messages. I have no way of knowing if there is any real progress unless I set my own arbitrary time limit for chkdsk to run. After 6 hours, I stopped the process. I am willing to try again for longer if necessary.

Further research tells me to run chkdsk /r instead of /f however upon attempting, the terminal windows hangs.

After letting chkdsk run for 6 hours, I restarted and attempted to try chkdsk on a faster Windows 7 VM via VirtualBox. Again, no dice. Windows hangs or tells me that the drive is in RAW format (but indicates NTFS in XP)...etc etc. Windows blah!!!!!

Question: Are there any solutions via linux/Ubuntu that could help with this issue? I am a dedicated Ubuntu user after leaving years or torment by Micro$oft Windows. Seems that M$ still has it out for me!

Penguin to the rescue? Where ya at Tux??

Any tips, feedback or help with this issue is appreciated!

P.S. Here is text copy of the error message that pops-up via Ubuntu when the drive is plugged in and I attempt to access the contents. Please note that I replaced my username with "xxxxxx" in the message.

Error Message:


"Error mounting /dev/sdb1 at /media/xxxxxx/My Passport: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb1" "/media/xxxxxx/My Passport"' exited with non-zero exit status 13: The disk contains an unclean file system (0, 1).
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
Failed to sync device /dev/sdb1: Input/output error
Failed to close volume /dev/sdb1: Input/output error"

---

### Post by weatherman2 on 2016-04-01
Could be the disk is failing.  Try checking the drive's S.M.A.R.T. status with GSmartControl (install in Ubuntu).  Look in the Attributes tab for any lines highlighted in red or pink - these are worrisome lines.  (Ignore messages like "pre-failure" which are just types of Attributes, not indications of failure.)

FYI, it's considered unsafe to stop chkdsk in the middle of trying to fix the filesystem.  Even if it takes hours.  Then again, it could be taking hours because the disk is about to fail.

I don't know of any better tools in Linux to fix NTFS filesystems than chkdsk - but if the disk is failing it's kind of irrelevant.

---

### Post by Yellow Pasque on 2016-04-02
> and immediately unplugged the drive and powered off the xbox.

You should have done it the other way around. Never disconnect an NTFS volume that's still mounted.

---

### Post by X-RED_Tech on 2016-04-02
> **Temüjin said:**
> You should have done it the other way around. Never disconnect an NTFS volume that's still mounted.

+1

---

