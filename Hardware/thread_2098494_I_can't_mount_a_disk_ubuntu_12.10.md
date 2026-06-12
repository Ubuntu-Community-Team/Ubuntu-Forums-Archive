---
title: "I can't mount a disk ubuntu 12.10"
date: 2012-12-26
forum: Hardware
---

### Post by Salvagluque on 2012-12-26
Hello guys,

I come with a classic problem, I can't mount a disk all of a sudden. there was nothing to trigger this error, I used this dis an hour ago, and then nothing. I have other disks working perfectly fine.The Disk is connected through a dual dockstartion with another disk connected and the only one not been able to be mounted it this one. I get this message any time I want to mount the disk.

Error mounting /dev/sdf1 at /media/salvador/2A0CF26A0CF23105: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdf1" "/media/salvador/2A0CF26A0CF23105"' exited with non-zero exit status 13: Failed to load runlist for $MFT/$DATA.
highest_vcn = 0x1b12f, last_vcn - 1 = 0x1b123
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdf1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Already tried the windows method with windows 7 in this very computer, but windows  instead of doing something through the chkdsk method, politely tells me to go ffformat the entire disk, which obviously I don't wanna. 
I remember Icould solve this without moving outof ubuntu, but I don't get to remember how I did it. I mean I have this problems long ago in ubuntu 7.10 and 8.04. So yeah, too much time to remember.

If anyone can help I really appreciate it.
Thanks.

Salvador

---

### Post by BertN45 on 2012-12-26
It looks like a hardware problem. 
Does the Ubuntu Disk Utility see the disk? If so look at the SMART Data and run the Benchmark test, the read only one. You do not have to mount the disk for that.
Else try to swap both disks to look where the error is in the connection/cable or in the disk itself. Cleaning the contacts may help.
You could also try the disc in another system.

---

### Post by Salvagluque on 2012-12-27
Ubuntu sees the disk, it appears in the partition manager apps I have, kde partition manager & mount manager. So, I think maybe dpkg has locked out this hdd. It has happened before, but never has shown me this message.

---

