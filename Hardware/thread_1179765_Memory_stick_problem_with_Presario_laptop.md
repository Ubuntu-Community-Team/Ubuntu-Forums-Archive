---
title: "Memory stick problem with Presario laptop"
date: 2009-06-06
forum: Hardware
---

### Post by samcan on 2009-06-06
I have a Compaq Presario 2592US that has been having some problems with the memory sticks. It came with two 256 MB sticks. Several months ago, when I restarted the computer, it sometimes would not display the Compaq logo at the BIOS, or if it displayed, it would be corrupted, and the machine would freeze.

I isolated the trouble to one of the memory sticks, and put in a 128 MB stick to replace it. Today, I decided to go back to trying to figure out what was wrong with the 256 MB stick.

I found that by putting the bad stick in one particular memory slot, the machine will freeze with a corrupted Compaq logo, but if I put it in the other, the machine may only display a black screen. Once I got the video to display (luck more than anything), I went into Memtest+, which is accessible from GRUB.

Here is the crux of the biscuit. I've run a gazillion passes on the sticks, and there are *no errors*! I suppose it could be that the bad bits on the stick are only in the area being used by the machine for shared video RAM, but doesn't that seem unlikely, considering the shared video RAM is only 8 MB?

Any thoughts on what I should do? It's an old laptop, and I don't want to spend a lot of money on it. I figured if I could isolate the bad bits using Memtest, I could use BadRAM to get around them.

---

