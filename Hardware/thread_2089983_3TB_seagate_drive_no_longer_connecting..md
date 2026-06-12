---
title: "3TB seagate drive no longer connecting."
date: 2012-11-30
forum: Hardware
---

### Post by PirateKarma on 2012-11-30
So I got a Seagate Expansion 3TB Hard Drive a few months ago, and well while I was backing up my files, Ubuntu 12.04 seemed to crash and I have to manually power off the computer by pressing and holding down the power button. However now when I try and connect the Hard Drive it no longer connects. I get the following error in Ubuntu only. When I connect it in Windows it works perfectly fine.  

> Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


I did what the message told me so, but nothing happened. When I put the commands into Windows it jus said drive in use. will check on next restart, but it never checks it.

---

### Post by oldfred on 2012-12-01
I think the /f was with XP's chkdsk.
Try again with /r
Change c: to your Windows 'drive' 
       chkdsk c: /r
    
You can use the following options:
 /p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by PirateKarma on 2012-12-02
> **oldfred said:**
> I think the /f was with XP's chkdsk.
Try again with /r
Change c: to your Windows 'drive' 
       chkdsk c: /r
    
You can use the following options:
 /p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

i tried the following and no errors were found, T.T.

---

### Post by oldfred on 2012-12-02
Does Windows see it as d: or e: and did you run with that "drive"?

---

