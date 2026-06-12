---
title: "Freezing"
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by BaidareW on 2009-02-15
Hi,
 I would like to install 8.10 on my Asus Z96S, but trying to install it freezes, mainly after disk partitioning. I tried alternative install (x86, x64) also. Now I was able to install but it freezes right after boot (few seconds I can do something) and most of the cases two indicators blinking (num lock and one more).

 I was able to install 8.04 some time ago. Now I have replaced HDD with new one 500GB and added extra RAM. Vista runs fine.

 Latest notices, getting these errors in booting stage with Linux Mint also:

 UCHI_HCD possible PCI Problems,
 host controller halted,
 buffer I/O error on deice sr0 
 and so on :)

 I have sata HDD, tried to set it as IDE or other option, robson module auto (in that other mode). 

 I will try other distro to make sure it is Ubuntu (kernel) related later if I will not be able to fix it.

---

### Post by BaidareW on 2009-02-16
The same with 9.04 alpha 4. Live CD installation hangs right after boot in first step. Two blinking lights.. kernel panic ?

I think some how HDD and more RAM affected this, because before this I didn't had problems installing linux on my laptop.

---

### Post by AllenGG on 2009-02-16
32 bit or 64 bit ? Which  version of 8.10  ?
Did Vista come preinstalled ?
Sata does not show up as IDE. Shows up as SCSI  device , scsi0. scsi1 etc

---

### Post by theozzlives on 2009-02-16
> **AllenGG said:**
> 32 bit or 64 bit ? Which  version of 8.10  ?
Did Vista come preinstalled ?
Sata does not show up as IDE. Shows up as SCSI  device , scsi0. scsi1 etc

SATA shows up as SDA, SDB, etc on my SATA laptop.

---

### Post by BaidareW on 2009-02-17
Thanks for your replay.

 I have tried all versions off 8.10 (also 8.04) including alternative install.

 Yesterday was booting debian 5.0 live CD, it also hanged but on booting I sow error message like "ACHI controller halt.. very bad" and few more like UHCI_xx something like this. Didn't remember exactly.

 I installed Vista my self and it works normally. Ubuntu works about to seconds from booting up (live CD the same, installation also with very rare exeptions). Strange that debian live CD also one time worked about minute before freezing and another right after boot.

---

### Post by BaidareW on 2009-02-17
Any ideas ?

---

### Post by BaidareW on 2009-02-18
In Opensuse forums helped me with this:

booting options:

brokenmodules=uhci-hcd
nolapic
noapic
pci=nomsi

So now I am able to install or boot linux :)

---

