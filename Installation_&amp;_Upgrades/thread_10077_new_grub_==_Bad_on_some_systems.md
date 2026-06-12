---
title: "new grub == Bad on some systems"
date: 2005-01-04
forum: Installation &amp; Upgrades
---

### Post by JackDog on 2005-01-04
I have recently encountered a problem with grub on hp laptops. Seems that newer versions of grub are unsuable on some systems that check for valid boot records before allow the boot to proceed. Basically what happens is, the bios will load and execute but tell the user no valid boot records can be found. There is no work around, doesnt matter if a partition is marked bootable or not.

This is what the bios prints to the screen in this case:
```
"Hard disk boot sector invalid" 

```

The livecd uses grub and will not work on such systems. The current install CD does however, I guess it uses isolinux.  When installing an ubuntu system,  expert mode has to be chosen so that the user can use lilo instead of grub. This system used to use grub and worked fine, however I dont know what version or what the difference is since the drive got wiped. 

I dont fully understand the reason for this problem, I only know from first hand experience.  If anyone knows of a workaround, let me know. All I have found when searching is other people who experienced the same problem but didnt find a solution.

---

