---
title: "Blank screen after initrd load with kernels &gt; 2.6.22?"
date: 2009-10-09
forum: Hardware
---

### Post by tavasti on 2009-10-09
I have very old Compaq Armada 1500c. I had ubuntu 8.04 running it, and decided to upgrade it. But unfortunately, no success. 

By modifying kernel command line, removing 'quiet splash' last line I could see was:

checking if image is initramfs .. it is 

After this, screen is blank. This same problem is with 8.10 (to which I upgraded my 8.04) and also 9.10 beta install cd. I think I saw this problem on some stage with 8.04 also, but then I just used older kernel (I think it was 2.6.22 that worked, 2.6.24 did not)

I've tried kernel command line parameters like vga=0, vga=1, vga=771, nofb but result is all time the same. 

Any ideas?

---

