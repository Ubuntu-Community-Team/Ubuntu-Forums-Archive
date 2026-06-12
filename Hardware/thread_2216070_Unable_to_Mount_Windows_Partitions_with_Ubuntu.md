---
title: "Unable to Mount Windows Partitions with Ubuntu"
date: 2014-04-09
forum: Hardware
---

### Post by Vinay Balraj on 2014-04-09
Hi guys, I've completely moved away from windows, but have dual booted with windows 8.1 as some apps like CAD wont run on Linux and need to turn back to windows.However, I'm facing few glitches with Ubuntu..


Well, coming to my issue, I own a Dell 15R 5521 laptop with Intel i7, 8GB RAM, 1TB HDD. And I'm also using cinnamon here as the interface is much neater.


Everything's working fine, except that I'm unable to mount windows partitions.

And for mounting partitions, this is what comes up when i try to mount


---------------------------------------------------------------------------------------------------------
"Unable to mount partition


Error mounting /dev/sda3 at /media/vinay/New Volume: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dm ask=0077,fmask=0177" "/dev/sda3" "/media/vinay/New Volume"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."
----------------------------------------------------------------------------------------------------------


I have tried booting to windows to make sure it was shut down and not locked. But still no vain.

---

### Post by Mark Phelps on 2014-04-09
You can't mount the Windows partitions when you're running Windows 8 because, even though you're not in it at the time, it still keeps the NTFS partitions mounted -- using a new form of Hibernation.

You have to go into Win8.1 and disable FastStartup.  Once you do that, when you boot back into Ubuntu, you should be able to mount the partitions. The price you pay for this is that, when you boot back into Win8 again, it will take a lot longer to startup.

However, that said, you should NOT mount the Win8 OS partition read/write -- as any changes you make to it from inside Ubuntu risk corrupting the file system and rendering Win8 unbootable -- making it real hard to fix.  You should only mount the Win8 OS partion "read only".

---

### Post by Vinay Balraj on 2014-04-10
Hi, @Mark, thanks for the tip. I disabled Fast Boot on windows 8 and was able to access the partitions. As I don't use it other than for some CAD drafting, 95% of the times laptop runs on Ubuntu, so I wouldn't care if something happens to the windows partitions or the data, nothing important there. You're a life saver. Thanks.. :)

---

