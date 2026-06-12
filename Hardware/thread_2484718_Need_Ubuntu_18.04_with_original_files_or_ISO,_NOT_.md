---
title: "Need Ubuntu 18.04 with original files or ISO, NOT updated kernel past 4.15"
date: 2023-03-07
forum: Hardware
---

### Post by basher522 on 2023-03-07
Hi.
 
 I got an older RAID card that can't be used on a machine with kernel past 4.15 (or maybe 4.16) so I can reach the data on it and move to either newer hardware
 or just go for SW RAID.
 
 No, I can't check or ask for a newer driver as the hardware is obsolete, which is kinda bad cos I got 2 of them and they have 16 ports each, pretty neat.
 
 Anyone know where I can get hold of all original files for this?
 I need ssh, vim, make and lots of other things so a place or a big fat ISO with them all so I can do this totally offline.
 All files need to be working with this version of kernel as it was when it was released.

---

### Post by guiverc on 2023-03-07
Ubuntu 18.04 LTS has two supported kernel stacks; the GA kernel stack is the 4.15 kernel, where as the HWE kernel stack changed to 4.18/5.0/5.3 before finally reaching its final 5.4.

The installation media used for 18.04 will dictate which kernel stack you're actually using by default.  For Desktop media that means you need to use 18.04 or 18.04.1, with server the default is the GA kernel stack (*though some let you select the kernel stack at install time* *but I don't know which ISO/release except some live-server* *ISOs*)

I'm largely a desktop user, and am aware that the Lubuntu *alternate* ISO used the GA kernel stack; that is still available for the next ~month at [https://cdimage.ubuntu.com/lubuntu/releases/18.04/release/](https://cdimage.ubuntu.com/lubuntu/releases/18.04/release/)  (*it was the last alternate ISO we released in April 2018*) though many Lubuntu ISOs can be found elsewhere too.

---

### Post by mIk3_08 on 2023-03-07
> **basher522 said:**
> Hi.
 
 I got an older RAID card that can't be used on a machine with kernel past 4.15 (or maybe 4.16) so I can reach the data on it and move to either newer hardware
 or just go for SW RAID.
 
 No, I can't check or ask for a newer driver as the hardware is obsolete, which is kinda bad cos I got 2 of them and they have 16 ports each, pretty neat.
 
 Anyone know where I can get hold of all original files for this?
 I need ssh, vim, make and lots of other things so a place or a big fat ISO with them all so I can do this totally offline.
 All files need to be working with this version of kernel as it was when it was released. you can just make it as an extended storage using enclosure so you can still use all the files from your old storage system to the new one. Regards and cheers.

---

### Post by basher522 on 2023-03-08
@guiverc, I'll have a look on that, thx

@mlk3_08, this seems nice, can you explain this enclosure more?
I only got the source for the drivers so I need to compile it if that makes any difference and as kernel 4.17 has changed it's handling of the old scsi initialization model and this don't have that, all kernels newer than 4.16 won't work.

@guiverc, just checked 18.04 server amd64 and the kernel-image file is 5.4 so seems it's not a GA stack.
Oh, I see both 4.15 and hwe 5.4. Maybe I can chose which to go for att installation time.

PS. Is it possible to add a tiny WM or light desktop to the server version?
Also if I want to add other packages like vim and make is that on the image or is that taken from an online source and if so, is that for the 4.15 version?

---

