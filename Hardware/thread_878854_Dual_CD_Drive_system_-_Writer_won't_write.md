---
title: "Dual CD Drive system - Writer won't write"
date: 2008-08-03
forum: Hardware
---

### Post by BJinMontreal on 2008-08-03
I have a Compaq Presario on which I've installed Hardy Heron.  The system came with two CD drives - one CD-ROM and one CD-RW.  My hardware issue is that the CD-RW drive although readable, is NOT writable.  I've searched through the forums trying to find a solution to this problem and the closest I came was finding a reply about changing the owner to root. This wouldn't help in my situation, because when I run checkdrive, the CD-RW drive is NOT found, despite me being able to play music CDs on it.

brian@brian-desktop:~$ wodim -checkdrive
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr1
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'COMPAQ  '
Identification : 'SC-140S         '
Revision       : 'SE04'
Device seems to be: Generic mmc CD-ROM.
wodim: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.

IF anyone has had this problem and fixed it, I'd love to hear about it.

---

