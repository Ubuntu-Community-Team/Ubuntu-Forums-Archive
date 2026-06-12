---
title: "NTFS Volume won't mount"
date: 2011-03-02
forum: Hardware
---

### Post by slashwannabe94 on 2011-03-02
Hello all, 

Background information 

I have just upgraded to ubuntu 10.10 64bit from ubuntu 10.04 32 bit. I previously was able to auto mount my NTFS external USB hard drive. But now that i am in ubuntu 10.10 i recieve this error when i try to mount it. 

This is the error code. 
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
-----------------------------------------------------------------------------------------------------------------------

I have also tried to use chkdsk /f in windows but receive another error from the command line saying

 "*Cannot lock* current drive. Chkdsk *cannot* run because the *volume* is in *use by another process*."

Any ideas on how to fix this? i need my data on that drive :( 

thanks, 

SlashWannabe94

---

### Post by mikewhatever on 2011-03-02
Have you tried Windows' safe mode?

---

### Post by slashwannabe94 on 2011-03-02
No i will try that now man. So safe mode, then ckdsk /f then reboot into linux and all should be well. I will give it a try : )

---

### Post by slashwannabe94 on 2011-03-02
I tried booting into windows 7 safe mode and running chkdsk /f from the cmd. But i still receive the same error. "Unable to lock Volume, being used by another process" --- help :( 

I know i ain't lost all my data but i need this fixed :( 

Thanks anyway dude :)

---

