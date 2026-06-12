---
title: "SCSI=IDE but RAID is a Promise ... and GRUB"
date: 2008-07-20
forum: Hardware
---

### Post by rated727 on 2008-07-20
As the thread title suggests something odd is happening in paradise.

Alternative thread title:  WTF??


Motherboard (BIOS) services on my WinXP/Ubuntu box includes a Promise Technologies IDE RAID - actually it links IDE2 and IDE3 to set up mirrored or striped RAID (IDE0 and IDE1 exist)

Boot options include the usual list of choices, floppy, CD, hard drive.  But, new-to-me was a toggle-choice between "Promise, SCSI" and "SCSI, Promise".  It took a while before the light went on.  

Choice "SCSI, Promise" sets the first drive on the first IDE channel as the boot device (before the IDE-RAID). 

*Personal note: I think that my Western Digital Caviar hard drive is very nice and can't imagine why anyone would suggest that there is anything SCUZZY about it. nudge-nudge-wink-wink*

Choice "Promise, SCSI" actually elevates the IDE-RAID above the first IDE harddrive in my boot sequence???  But that would never actually happen ... would it?

(in the voice of P.T.Barnum)... Welcome Ladies and Gentlemen.  Step right up and watch as Ubuntu installs GRUB to a RAID!!  Mothers, please hold your children back to a safe distance, this will be a bit messy.

"Only two things are infinite, the universe and human stupidity, and I'm not sure about the former." --Albert Einstein
"The reason for life is to provide time for recovery between explosions." -- rated727

---

