---
title: "Tablet PC dual boot XP Tablet Ed and Ubuntu won't boot"
date: 2008-06-30
forum: Hardware
---

### Post by tomaszdunn on 2008-06-30
I maanaged to get a dual boot working on my FUjistsu Siemens T4010D - and got the stylus workign in ubuntu with it as well. However recently Ubuntu suddently locked up,so annoyed I gave it a hard reset, and now it won't boot into either and the boot slector doesn't come up - it just flashes the bios and stays on a flashing _. Some one had a look and suggested a partition table or MBR fault. I managed to get a boot disk up and am uisng testdisk - however on analysise it keeps coming up that no partions can be found. 
I'm not enitrely sure if i have the correct number on sector and head settings correct and not completely sure what i'm looking for.
On the analysis it finds either nothing or says:

The following partition can't be recovered
Partition             Start     End  Size in Sectors
D HPFS - NTHS     0   1 1 45007  7 55   4567489

Now I'm not particularily clever enoguh to know what this means but there was more then one partion on the disc and i don't know why the ubuntu partion is not showing up either. (The hard disc is 40gb). Any hep would be apreicated - I don't really want to have to wipe the disc and start again.

---

### Post by Fr0z3n.0n3 on 2008-06-30
I'm hardly an expert, but the first thing I'd check is if the file systems are still intact. I don't think a single hard-shutdown could do it, but in my experience its best to rule these things out early.

Try popping in a LiveCD and opening your partitions, make sure they are accessible, etc. If they aren't... well, there are some tools for recovering files off of damaged partitions, but you might stuck reinstalling Ubuntu. If neither partition appears damaged, I'd try booting into either OS using [SuperGrub]("http://www.supergrubdisk.org/").

---

