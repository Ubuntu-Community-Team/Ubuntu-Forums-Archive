---
title: "Unable to boot after upgrade to 9.04"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by handman003 on 2009-07-06
I just did a network upgrade to install Jaunty and now Ubuntu won't boot at all. The boot sequence ends with "Kernel panic - not syncing: Attempted to kill init!" My kernel is version 2.6.28-13 generic if that helps at all.

Just before the Kernel panic line, the console reads:

```
[<c04ff1b2>] error_code+0x72/0x80
[<c04f0000>] ? quirk_isa_dma_hangs+0x39/0x46
Code: (insert here a huge string of characters seperated into groups of two by spaces)
EIP: [<c0193a80>] prep_new_page+0xb0/0x140 SS: ESP 0068: dec6dce4
---[end trace a996bbe249cbbe43]---
note: init[1] exited with preempt_count 1
```

Then "Kernel panic - not syncing: Attempted to kill init!" shows and the Caps Lock and Scroll Lock keys on my keyboard begin flashing. The computer becomes completely unresponsive to everything except for the power button at this point.

Help/advice would be appreciated. :)

EDIT: Booting into any earlier kernel versions results in a distorted image during the bootup sequence, from which I can not enter the console. I can boot into older recovery kernels, however.

---

### Post by handman003 on 2009-07-06
I am also unable to boot using a 9.04 Desktop Edition live CD. It gives a similar error also ending with "Kernel panic - not syncing: Attempted to kill init!"

---

### Post by docetrago on 2009-07-08
Same annoying error message here. Having to reboot for at least 3 times in order to login. What's up, guys ?

---

### Post by earthpigg on 2009-07-08
if you are getting a kernel panic *_even from the live cd_*, when *_the exact same live cd worked before on the exact same hardware*_, then it is probably a hardware failure of some sort. :(

edit: does the 8.04 CD work? 8.10?

---

### Post by docetrago on 2009-07-09
> **earthpigg said:**
> if you are getting a kernel panic *_even from the live cd_*, when *_the exact same live cd worked before on the exact same hardware*_, then it is probably a hardware failure of some sort. :(

edit: does the 8.04 CD work? 8.10?

I upgraded from 8.10 to 9.04. I replaced the 2 x 512 MB RAM with 2 x 1024 MB since the 8.10 version. Booting from HD.

Maybe reinstalling 9.04 might troubleshoot this, I think. I'll perform a disk checking for errors / corrupted boot files...

Your comments are welcome.

Thanks for posting.

---

### Post by docetrago on 2009-07-09
:p

I'm back to tell you that's fixed.

My old PC has a ASUS P4S8X-MX motherboard, with 2 GB  RAM ( a pair of Kingston Value RAM KVR400X64C3A/1G ).

I reinstalled Ubuntu from the Live CD. When partitioning, I setted a SWAP area of 4 GB, right after the Ubuntu boot partition.

I googled a lot and found some posts suggesting a good SWAP partition size being about 2 times the RAM capacity. Is it correct ?

It worked fine for me, no more kernel panic error messages ( at least up to now ).

Your comments are welcome.

):P

---

### Post by earthpigg on 2009-07-09
glad things worked out for you. sorry we weren't of more help.

---

