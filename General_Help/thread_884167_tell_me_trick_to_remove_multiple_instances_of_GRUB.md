---
title: "tell me trick to remove multiple instances of GRUB"
date: 2008-08-08
forum: General Help
---

### Post by howhy on 2008-08-08
I just want to keep Win XP & gOS as my OS on lappy, i already had Kubuntu, that now i am unable to remove from computer , i am doubtfull that MBR points to GRUB first then it goes to boot.ini in c:\ drive, 

all drives are NTFS except where Kubuntu is installed is Ext3 , and i want to remove kubuntu and install gOS on it, I want a clean OS selection menu ...

i hope u help me out fast

---

### Post by Oldsoldier2003 on 2008-08-09
Moved from Tutorials and Tips moderation queue to General help.

---

### Post by caljohnsmith on 2008-08-09
If you are going to have multiple operating systems on your HDD, you need to have some sort of boot manager, and one of the best is Grub. I don't know if gOS comes with a boot manager or not, but if it does, you may be able to configure it to boot whichever OS you want on startup. If it doesn't have a boot manager or is not able to be configured to boot other operating systems, then you could install Grub into its own dedicated partition (a really small, 50 MB partition is all you need), and use that to manage booting all your operating systems.

---

