---
title: "Disable MBR when adding a scsi device to Ubuntu"
date: 2015-11-11
forum: Hardware
---

### Post by per6 on 2015-11-11
Is there a way to disable unbuntu/linux to read mbr (start sectors) when adding a scsi device into linux? 

In Ubuntu 8 Server it was possible to stop udev and then it did not read the start sectors, but newer versions i can't find any solutions.

---

### Post by per6 on 2015-11-23
Is it wrong forum category i'm in to ask this question? if so plz admin plz move this thred to a better place.

---

### Post by oldfred on 2015-11-23
I can move to server sub-forum if you like. Do not know if better or not.
You also can bump once per 24 hours as many just look at recent posts. Best not to do at exactly every 24 hrs as we are worldwide and many users in other parts of the world may also have a solution.

Not sure why you need to disable MBR, but I do not know servers. 
Is this RAID and you are disabling the RAID boot, not really the MBR? As MBR is really controlled by BIOS, not installed system.

---

