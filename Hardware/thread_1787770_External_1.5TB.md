---
title: "External 1.5TB"
date: 2011-06-21
forum: Hardware
---

### Post by Platynum on 2011-06-21
I was transfering movies on some hard drives, during the transfer i tripped and pulled the plug on one of the hard drives. I'm now getting "Unable to mount Elements" it says 
 
 
I'm running 10.04 ubuntu on an HP g62 i don't have internet on the linux laptop the device still works because i connected it to my friends laptop (windows XP) and could view everything on it
 
 
 
 
 
 
Error mounting: mount exited with exit code 13: $MFTMirr
does not match $MFT (record0).
Failed to mount '/dev/sdc1':Input/ouput error
NTSF is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter 
is very
important! If the device is a SoftRAID/FakeRAID then first
activate
it and mount a different device under the /dev/mapper/
directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmarid'
documentation
for more details

---

### Post by psusi on 2011-06-21
Run scandisk/chkdsk on it from windows.

---

### Post by Platynum on 2011-06-21
Tried that, didn't work rebuted twice after I ran that command...

---

### Post by psusi on 2011-06-21
You can scandisk from windows and it found nothing wrong?  Check the last few lines of dmesg after you try to mount it.

---

### Post by LowSky on 2011-06-21
properly unmount (remove safely) the drive in Windows..

the try it again in Ubuntu

---

### Post by oldfred on 2011-06-21
Chkdsk does not fix everything on one pass. You have to rerun until no errors.

chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
Rebuilding An NTFS Boot Sector On An NTFS Partition

---

