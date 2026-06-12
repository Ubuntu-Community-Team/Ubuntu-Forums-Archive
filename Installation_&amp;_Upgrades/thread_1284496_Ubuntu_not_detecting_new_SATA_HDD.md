---
title: "Ubuntu not detecting new SATA HDD"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by mr alex on 2009-10-06
I have recently built myself a new computer which has been working fine with 9.04 using a 120gb ide HDD, but today I tried to install the 64bit version of 9.04 on a new 100gb SATA2 HDD. All steps went fine until setting the partition when Ubuntu could not find any disks. I am stumped with what the problem is because by all accounts it seems that SATA3 is supported and widely used.

Therefore I am wondering if the issue is to do not with t he HDD but the motherboard. It is a Gigabyte GA-MA785GMT-UD2H. When I boot (even using the ide HDD which I want to replace) before loading Grub is comes up with: 

```
Verifying DMI Pool Data.....
AMD Data Change... Update New Data to DMI!
```I feel that I am now entering territory that is getting above my head, any help or advice would be greatly appreciated.

---

### Post by presence1960 on 2009-10-06
you need to go into BIOS and see if the new SATA HDD is recognized by your BIOS. If it isn't recognized in BIOS no OS is going to see it. Refer to your motherboard's documentation for specific steps to take.

---

