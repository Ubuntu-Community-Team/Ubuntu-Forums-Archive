---
title: "4 GB RAM reported as 3895 MB"
date: 2012-09-07
forum: Hardware
---

### Post by Nopposan on 2012-09-07
Hello Ubuntuists.

I am trying to revive a Dell Studio 1558 with Intel i3 Core processor. Trying to use Windows gave me a blue screen with an error message CONFIG_INITIALIZATION_FAILED and a STOP code of 0x00000067. This seems to imply a possible problem with RAM or cache. I checked the cache using a memory testing software from bootable CD, and it's fine. I don't have any software suitable for testing the RAM thoroughly and giving a report; when I try MemTest86 it reports no errors but only gets 46% of the way through before it freezes completely, and I think that's because it's only experimental for multiple processors.

The 4GB RAM is two 2GB (2048 MB) DDR 3 cards. When either card is inserted by itself in either slot the BIOS reports 1911 MB of extended memory. When both cards are inserted the BIOS reports 3895 MB of extended memory! The BIOS reported extended memory seems whacky to me; could someone please let me know if I'm correct in thinking that the BIOS is misreporting the RAM? ("Extended memory" is the same as removable RAM, right?) Also, please let me know if there's something I can do to fix the issue. (Obviously, replacing the RAM or upgrading the BIOS would be preferable to purchasing a new motherboard. Oh, the machine is not on warranty.)


Thanks!

---

### Post by LiamOS on 2012-09-07
I'm not sure, but it might be that the BIOS reserves a certain amount of memory for itself. I seem to recall seeing something to indicate that sort of thing while compiling kernels.

---

### Post by Epodx64 on 2012-09-07
My guess would be you have an integrated graphics card on your motherboard I have an Intel GMA 4500 I have 4GiBs of DDR3 Ram installed to but 130Mb goes to the onboard video so it only reports 3.7GiBs

---

### Post by Nopposan on 2012-09-07
Yes, that explains it. Thank you.

Unfortunately, the memory is not the issue. Rather, it seems like there's a problem with the motherboard. :-(

---

