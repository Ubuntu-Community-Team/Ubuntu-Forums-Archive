---
title: "Can't mount my hard drive."
date: 2014-09-13
forum: Hardware
---

### Post by santiagovulliez on 2014-09-13
Please, help! 
I have 2 hard disks, the one i'm using right now, 300 gb, and another one, of 250 gb.
The 250 gb one is called "Mi Pc" And Ubuntu recognises it but shows me this error when i try to mount it 

Error mounting /dev/sdb1 at /media/santiago/Mi pc: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdb1" "/media/santiago/Mi pc"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

I have a lot of important information in it, and i need to recover it. Also, i could really use the hard disk...
If anyone knows what i can do i'll appreciate it.
Sorry if i made any spelling mistakes, or posted this in the wrong place... i don't speak english, and it's the first time i post in this forum
Thanks!

---

### Post by yancek on 2014-09-13
Since it is a windows (ntfs) filesystem, have you booted windows and run chkdsk as suggested in the output?
Are you using RAID?

---

### Post by santiagovulliez on 2014-09-24
I'm not using RAID.
Sorry i answered late, but i was looking for a windows computer. Believe it or not, i don't have one... My only computer has ubuntu, and i can't find anyone who could lend me a windows one at least for another month...
Is there any way i can at least recover the data that's in that hard drive? So i can format it afterwards...

---

### Post by Mark Phelps on 2014-09-24
Need to know if the drives cames from a Windows PC, and if so, what version of Windows was running?

---

### Post by santiagovulliez on 2014-09-24
I think it came from a computer with Windows Xp

---

### Post by santiagovulliez on 2014-09-24
Solved! I recovered the files with testdisk
I had issues understanding how it works because i am a spanish speaker, but it worked great.
Thanks!

---

