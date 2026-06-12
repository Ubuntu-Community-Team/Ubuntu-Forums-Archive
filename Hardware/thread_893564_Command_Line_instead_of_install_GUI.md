---
title: "Command Line instead of install GUI?"
date: 2008-08-18
forum: Hardware
---

### Post by KeithCostin on 2008-08-18
Hi all. I'm a total linux n00b, so please bear with me. I just got an old laptop from a buddy and i'm trying to install ubuntu on it, but I'm having a big issue. Whenever I try to either run ubuntu live from the CD or install, all I get instead of the gnome GUI is a strange command line. Instead of the normal command line stuff it says (initframs). I've tried Kubuntu and Ubuntu 8.04, but to no avail. The laptop I'm running on is a 12" Averatec laptop, 1.66 GHz Intel Centrino, 1GB of ram, and some kind of Intel Extreme Graphics 2 M onboard thingy for graphics. Any ideas? Thanks! :guitar:

---

### Post by sopsaare on 2008-08-18
There is 3 reasons why it might do that. 
1. The CD is faulty.
2. The laptop is faulty. (use memtest for the beginning)
3. The apic (or apci) is not working, there is a way to disable it from command line option at the grub.

---

### Post by doas777 on 2008-08-18
> **KeithCostin said:**
> Hi all. I'm a total linux n00b, so please bear with me. I just got an old laptop from a buddy and i'm trying to install ubuntu on it, but I'm having a big issue. Whenever I try to either run ubuntu live from the CD or install, all I get instead of the gnome GUI is a strange command line. Instead of the normal command line stuff it says (initframs). I've tried Kubuntu and Ubuntu 8.04, but to no avail. The laptop I'm running on is a 12" Averatec laptop, 1.66 GHz Intel Centrino, 1GB of ram, and some kind of Intel Extreme Graphics 2 M onboard thingy for graphics. Any ideas? Thanks! :guitar:

you may need to install via the alternate install CD. it is available at the main download site, but you have to click a smaller link. look arround and you shouldn;t have any trouble finding it.

I had to use the alt cd from my HP laptop with 7.04. it's worked just fine with the live CD in 8.04 though, so things keep improving.

you also may want to try disabling APCI. there are  afew threads on that topic. 

good luck,
franklin

---

