---
title: "Gutsy - Install problems on Compaq EVO N620c"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by ldnz on 2007-10-25
Hi,

I successfully installed Ubuntu 6.06 LTS on this laptop last week and has been great, but now I am trying to install the latest Gutsy release and am running into problems.

When I insert the cd, it will boot into the livecd, or any of the other modes, but it takes a very long time, and throws up the following messages enroute:

197.22 buffer i/o error on device fd0, logical block 0
235.358 buffer i/o error on device fd0, logical block 0

and the floppy disk light (there is no drive in this machine) is stuck on until past these messages. 

I have checked both the .iso and the cd itself on other machines and have come back with no errors. I haven't seen this same problem on other machines. 

Once livecd booted if I click on install I can work my way through the options (with long pauses when it starts examining the partitioning) but on telling it to start the installation it hangs at 15% (inspecting hard drive?). Oh and at this point the floppy drive light has come back on.

Is there a way to disable the floppy drive altogether? Am I thinking on completely the wrong lines?

Cheers,

Ben

---

### Post by ldnz on 2007-10-25
Belay the last - I was confusing two seperate problems. The reason the install itself was failing was due to partitioning. When I cleared the partition table and set it up manually all was well.

---

### Post by lazyart on 2007-11-05
Disable the floppy drive in system BIOS (F10 when powering up).  I run Gutsy on my N620c pretty smoothly.

---

