---
title: "external hd ntfs wd 1terra"
date: 2010-07-30
forum: Hardware
---

### Post by aircos on 2010-07-30
hello,

when i try to mounth it i get the following error

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

altho when i use disktools it reads the disk accurate on the model and evrything (WD 10EACS External)
and yes i cant program at all and i always use the graphical interfaces to get somewhere (failing bigtime on this one)
so euh yeah , HELP plz

(iam positif i installed the ntfs drivers for linux)

cheers peeps

---

### Post by aircos on 2010-07-31
anybody??

(is there any way i could force remove a file from the disk useing the kernel and if yes, how? )

---

