---
title: "How do I remove ubuntu 8.04?"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by jackpotmoney on 2009-10-26
I looked everywhere for a place to show me how to delete it.
They said to go to the Synaptic Manager and search something with linux and it didn't work.

I just downloaded ubuntu 9.04 and wanted to remove ubuntu 8.04.

I download Ubuntu 8.04 with a CD. I did not download it into windows.
When I turn on my laptop it says Ubuntu 8.04, Windows Vista Load, and Ubuntu 9.04,

I want to get rid of 8.04.

Thanks!:D

---

### Post by stlsaint on 2009-10-26
you will want to format the partition that 8.04 is on, and if its the menu.lst you want to edit than you will want to remove the 8.04 stanza from your menu.lst in:
```
 gksudo gedit /boot/grub/menu.lst 
```
 
in that file you will see your stanzas for all OS's that grub as added and you will be able to remove the 8.04 entry. 

**NOTE: I recommend you format the partition first as that will remove 8.04 a safer way.**

---

### Post by jheaton5 on 2009-10-26
> **stlsaint said:**
> **NOTE: I recommend you format the partition first as that will remove 8.04 a safer way.**

If I understand correctly you now have a tri-boot set up.  If that is so, then what stlsaint says is correct.

---

