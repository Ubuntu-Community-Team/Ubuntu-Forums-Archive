---
title: "Uefi"
date: 2012-03-04
forum: Hardware
---

### Post by stuartbh on 2012-03-04
Ubuntu and Linux experts:

I am currently playing with a Compaq CQ62 231NR and am trying to determine its fitness for deployment of an EFI + GPT bootable environment for both Windows and as well Ubuntu.

The CQ62 231NR's firmware variant is "F.29". Any idea of this firmware supports UEFI or EFI?

The CQ62 does instantiate an MBR boot environment in the instant, but I am desirous of amending its factory configuration such that:
 
(a) has its internal DASD formatted using GPT partitioning scheme
(b) can be capable of booting Windows 7 via EFI (if possible)
(c) Making sure that the "HP Tools" partition is able to be retained or reappointed to function properly
(d) Ubuntu could be installed onto GPT and be booted via EFI
(e) Of note, I have no concern for the ability to use "F11 - Recovery Mode", as I do keep system image backups via Windows

Ubuntu questions:

What is involved in appointing an environment capable of booting Ubuntu 11.10 or the forthcoming release of 12.04 using a GPT formatting scheme in congress with EFI booting procedures?

What level of compatibility or lack thereof becomes of issue when Windows 7 is also going to be placed thereupon the same DASD as the Ubuntu environment set forth in the preceding question?


Windows question (should anyone be aware):
 
If a full reinstallation of Windows 7 is requisite, and the HP Recovery DVDs I made when I initially got the system are not going to function for this purpose (to restore to a GPT partitioning scheme), then I am interested to understand if I can use a regular olde Windows 7 installation DVD to reinstall and have any level of expectation that such a reinstallation will seem "genuine" from a Microsoft point of view?

Thanks in advance.
 

V/R,
 
Stuart

---

