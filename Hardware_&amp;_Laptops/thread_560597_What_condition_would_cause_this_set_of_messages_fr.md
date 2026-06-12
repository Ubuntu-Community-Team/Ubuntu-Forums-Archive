---
title: "What condition would cause this set of messages from this set of kernels?"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by OfficeLinebacker on 2007-09-26
Hi.

Patient presents with unable to boot syndrome.  
GRUB comes up fine, but no kernel will boot.  Installed OS is Feisty 7.04 server with kde installed over top.  Installed kernels(with error messages):

2.6.20-16-server~
--recovery*
2.6.20-16-lowlatency~
--recovery
2.6.20-16-generic
--recovery
2.6.20-15-generic~
--recovery
2.6.17-12-server+
--recovery*
2.6.17-12-generic*
--recovery
  2.6.15-29-amd64-server*
--recovery*
2.6.15-29-amd64-generic*
--recovery
2.6.15-26-amd64-server*
--recovery!~


Legend:
* crc error; system halt
+ Hardware Error: CPU0: Machine Check Exception
~kernel panic-not syncing: VFS: unable to mount root fs on unknown block
!crc error; VFS: cannot open root device "UUID=baa12cade-faa3-etc" or unknown-block(0,0) Please apppend a correct "root=" boot option.

Hardware is AMD 64 X2 3800+ on an unidentified ASUS board.  Boot HD is the primary master IDE.  There are also four SATA drives connected which the patient has been struggling to recognize.

Last known use was a system lock-up while loading multiple pages in Firefox.

Thoughts?

---

### Post by Linicks on 2007-09-26
> * crc error; system halt
+ Hardware Error: CPU0: Machine Check Exception

That doesn't look good.  Maybe CPU got too hot and is damaged.

The system lock up with FF was maybe the symptoms of the cpu overheating and dying.

Nick

---

### Post by OfficeLinebacker on 2007-09-26
> **Linicks said:**
> That doesn't look good.  Maybe CPU got too hot and is damaged.

The system lock up with FF was maybe the symptoms of the cpu overheating and dying.

Nick

Uh Oh.  So is the next step to order a new CPU or is there any further testing to be done?

Jonathan

---

### Post by tdrusk on 2007-09-26
> **OfficeLinebacker said:**
> Uh Oh.  So is the next step to order a new CPU or is there any further testing to be done?

Jonathan

Try a live cd to make sure something isn't corrupt on the hdd.

---

### Post by OfficeLinebacker on 2007-09-27
> **fuzzyhair said:**
> Try a live cd to make sure something isn't corrupt on the hdd.

OK, I will try it.  Will report back.

---

### Post by OfficeLinebacker on 2007-09-27
Well, the live CD boots up fine.  When I chose repair, it went through the keyboard stuff, found the cd, and then the kernel freaked when it was loading modules...i could tell because the right two lights of the keyboard (caps lock and ?) started blinking.  

I'll try again with installing just to see how far I can get into that process.

j

---

### Post by OfficeLinebacker on 2007-09-27
The install process failed at the loading additional packages stage when loading nic- something.

Right now I am running memtest from the boot cd menu.

---

