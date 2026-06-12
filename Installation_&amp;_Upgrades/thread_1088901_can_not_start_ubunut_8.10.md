---
title: "can not start ubunut 8.10"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by bukormen on 2009-03-06
I have installed ubuntu 8.10 on ACER PC, but when I try to boot this message comes up:
"[0.456028] ... MP-BIOS bug: 8254 timer not connected to IO-Apic
[0.456028] Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the `noapic` option
[0.456028]"

Does anyone know what has happened and/or how to boot with "the `noapic` option"? Maybe I have to burn a new CD?

---

### Post by avtolle on 2009-03-06
See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) on how to use boot options (noapic being one of them, and the one you need to use, it appears).

---

### Post by bukormen on 2009-03-06
I am now inside ubuntu, but when I wish to install a problem arises at partion stage. When I install direct from CD it is OK (apart from apic problem...), if I install from inside ubuntu I fair I might delete Vista. It is unclear where ubuntu will be installed. I wish to install ubuntu in partion D, which does not come up on the menu.

If I install ubuntu from CD how do I avoid the apic problem? 

From what I have seen Ubuntu is very good, better than Vista. (But I would like to keep vista incase something happens..)

---

### Post by wpshooter on 2009-03-06
I have been receiving the 8254 timer bug message on one of my older computers when trying to install either Intrepid or Jaunty or when I try to run the CD integrity check function from either of those 2 O/Ss.

Also, please note that when I tried the noapic parameters as mentioned in one of the prior responses, it made no difference, I still got the 8254 timer bug message.  I have reported this as a bug and have sent in the requested information for someone to troubleshoot the bug, but as far as I know, the bug still has not been fixed.  Please note that I do not get the 8254 timer message when installing versions of Ubuntu prior to Intrepid, so this tells me that this is something wrong with the latter versions of Ubuntu and not a problem with my or your computers.

Good luck.

---

### Post by bukormen on 2009-03-06
I took a chanche and installed ubuntu. Everything looks OK. I think vista survived too! The partitions bit could maybe have been a bit easier to use...

---

