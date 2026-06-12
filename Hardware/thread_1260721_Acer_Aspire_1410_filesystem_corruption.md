---
title: "Acer Aspire 1410 filesystem corruption"
date: 2009-09-07
forum: Hardware
---

### Post by crumpledfarm on 2009-09-07
Installed Ubuntu 9.04 amd64, initially all functions working as reported but the system fails to survive system update and reboot with the filesystem becoming corrupted irreparably. 

Also attempted Fedora 11 amd64 install which fails to mount partitions after formatting and install fails. Vista and Windows 7 seem to be working fine. Have not seen this issue reported elsewhere.

Attempted installing using a different system on the drive and the system works until the drive is moved back into the machine where the filesystem is again corrupted.

Updated to latest bios following inital trouble with no improvement. I've installed approximately 10 times from different install media with the exact same outcome.

Sometimes filesystem errors appear in dmesg but I haven't seen anything relevant in /var/log/messages. Totally stumped on this one :(

Oh, forgot to add that all described issues were experienced with the bios set to IDE mode and not AHCI.

---

### Post by juliansuddaby on 2009-09-08
I was getting very frustrated with HD errors before switching to IDE mode (which you said you already did) and then just getting pissed off and totally reformatting the whole drive (wiping Vista). Maybe you tried that already -- I don't know.

I suspect that the way Acer formats the HD is a bit weird (it's got one of those hidden recovery partitions -- could be that?).

---

### Post by crumpledfarm on 2009-09-08
Yeah, I wiped the partition table at some point in there. Are you running amd64 though? I installed Ubuntu 32-bit yesterday and it seems to be doing fine. 

I'm running windows 7 x64 with no trouble, maybe some strange bug. I'm going to try Karmic Koala today, will report back on the results.

---

### Post by crumpledfarm on 2009-09-13
Karmic amd64 is working beautifully, crisis averted

---

