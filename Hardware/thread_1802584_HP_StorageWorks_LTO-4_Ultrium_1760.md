---
title: "HP StorageWorks LTO-4 Ultrium 1760 ?"
date: 2011-07-12
forum: Hardware
---

### Post by MrEgg on 2011-07-12
Hi all,

Is anyone out there using an HP StorageWorks LTO-4 Ultrium 1760 on a Ubuntu machine? HP says it is compatible with RedHat and Solaris - what about Ubuntu? Additionally, does it work well with Bacula or is there a recommended backup?

Feedback greatly appreciated.
TIA,
Egg

---

### Post by KewlEugene on 2012-06-18
Yes I boot Ubuntu on a HP Desktop and use it with the HP 1760 SAS External.

You have to install **mt-st** to add additional mt support.

The tricky part is the SAS card. I think only NON-RAID cards work. I finally got an IBM 25R8071 SAS HBA to work.

---

