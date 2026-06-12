---
title: "Unable to mount My Passport + error with usbtransfer"
date: 2011-08-22
forum: Hardware
---

### Post by ventrikolo on 2011-08-22
So from out of nowhere this problem surface with my external WD Passport hardrive. Its been working very well before. I was going to use it and plugged it in and get following error message:

____________________________________________________________________________
Unable to mount My Passport
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
____________________________________________________________________________

Another problem that started occuring after this is when I turned to another way of storing the movie on my usbstick instead. There i get the problem that the filetransfer bar stops in the very end for good, even though just sometimes the whole file has actually been transfered anyway

---

### Post by IcarusR on 2011-08-22
> NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important!

So have you tried this ?

---

