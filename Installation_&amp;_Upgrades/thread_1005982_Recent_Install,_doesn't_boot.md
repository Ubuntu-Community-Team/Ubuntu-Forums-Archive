---
title: "Recent Install, doesn't boot"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by JAJB92 on 2008-12-08
I installed Ubuntu yesterday, my first time trying any Linux whatsoever, and resolved an issue I had with ownership of one of my hard drives.

Today, after being on for a short amount of time, downloading updates and a couple of files (.rar files), I noticed my hard drive that I was having an issue with was not displaying any files, and saying it was "Read only".

I restarted my computer, hoping to resolve the issue, to find that it no longer boots, and gives me a long error message:

CLIENT MAC ADDR: 00 04 4B 06 5F DD GUID: 669A0C20-0008-46A7-DA11-FDAG807EDEC6
DHCP......

And stops there with a spinning /.

I am currently running from a live disk.

I am hoping someone can shed some light on this problem, because to my knowledge I did not change any essential files.

---

### Post by Mark Phelps on 2008-12-09
Sounds like you may have more than one OS on your machine. How about opening a terminal from the LiveCD and doing "sudo fdisk -lu" (that's a lower-case ell, not a one) and posting the results here so we can see what partitions are on your box.

---

