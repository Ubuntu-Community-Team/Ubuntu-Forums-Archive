---
title: "GRUB during runtime"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by fluffie on 2009-02-24
hi, i was reading up on GRUB (short of looking at source), and was wondering if GRUB might be vulnerable to any runtime attacks.  i am wondering what kinds of input does GRUB take.  

as far as i know, GRUB stage 1 resides on the MBR and it is hardcoded to find stage 2, and the stage 2 will load grub.conf. how does the code in stage2 access grub.conf? how is a file accessed? does it need to read certain records etc? sorry for digressing...

---

