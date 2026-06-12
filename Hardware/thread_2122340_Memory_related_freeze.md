---
title: "Memory related freeze"
date: 2013-03-04
forum: Hardware
---

### Post by ManamiVixen on 2013-03-04
For some reason, if I boot ubuntu 12.10 64bit on 4GB of ram, it freezes exactly 5 seconds after log in. The only fix I could find was taking out a stick, leaving 2gb in. There Ubuntu worked fine. I know it isn't the ram, memtest gave it the clear multiple times for both 2GB sticks. Only way to get all 4GB's working was to update to the 3.7 or newer kernel. Is this a Kernel issue? Do I have remove a stick everytime I reload Ubuntu? Help please.

---

### Post by tgalati4 on 2013-03-04
Some motherboards need to be declocked to handle a full RAM load.  Do some research on your motherboard chipset.  What are the current timings that you are using for your RAM--4-4-4-12?  Try changing to 5-5-5-18.  Does memtest pass if all 4GB are installed?  Did you run it for 30 complete cycles (might take overnight).  Some memtest versions have a bug that causes a failure at 129MB during test #7.  You can ignore that error if it comes up.

---

### Post by ManamiVixen on 2013-03-04
I checked my ram against my board. They are compatible. I have a Gigabyte G41M-ES2L and the ram is 2x2GB of G.Skill DDR2 800MHz 5-5-5-15. But as I said. The computer freezes only on kernels older than 3.7. In fact, I'm running on the ram now with said 3.7 kernel. Just don't want to have to pull a stick out every time I reload the computer or need to run a livecd.

---

### Post by tgalati4 on 2013-03-08
What chipset is on the motherboard that controls the RAM?  Do some research on that chipset and you may find a bug that was fixed in 3.7 kernel.  Does it make a difference booting a Live DVD of 32-bit vs 64-bit Ubuntu?  4GB is at the max that 32-bit can address, so there may be an issue between the motherboard chipset and older kernels.

---

### Post by ManamiVixen on 2013-03-08
It's fixed now. Miss-seated memory was to blame. Computer froze when ubuntu started using the second stick. Reseated the memory and it works now. Could of sworn I put them in correctly evey time I tested them.

---

