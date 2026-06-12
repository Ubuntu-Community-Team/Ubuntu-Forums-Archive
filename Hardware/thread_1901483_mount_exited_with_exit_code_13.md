---
title: "mount exited with exit code 13"
date: 2011-12-28
forum: Hardware
---

### Post by LasseNC on 2011-12-28
Hello! 

I've been spending the night trying to redistribute space on my harddrive, which has led me to reinstall ubuntu.

Currently I'm running Windows 7 and Ubuntu as dualbooting.

Right now, when starting windows it enters a repair state, finishes that and reboots.

Also, ubuntu is giving this error.

"Error mounting: mount exited with exit code 13: Corrupted file $UpCase
Failed to mount '/dev/sda4': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
"

How should I proceed?

I've used the search function, but the resolutions all seem "situation"-specific.

---

### Post by LasseNC on 2011-12-28
gparted tells me to do a checkdisk /f, but I cannot do this since I can't boot it up.

---

