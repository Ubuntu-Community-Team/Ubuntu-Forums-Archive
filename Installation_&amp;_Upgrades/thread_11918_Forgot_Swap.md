---
title: "Forgot Swap"
date: 2005-01-20
forum: Installation &amp; Upgrades
---

### Post by rbrugman on 2005-01-20
Hello,
I installed Ubuntu and am really enjoying it.  I did, however, forget to set a SWAP drive.  I have 3GB left on my drive that is unused, but how do I go about adding the swap drive without reinstalling?

Thanks,
Robert

---

### Post by Rule on 2005-01-20
I don't think you need one if you have enough ram, I know when I run top my swap is never used no matter what I do and I only have 512  :D

---

### Post by az on 2005-01-20
You manually partitioned your drive with the installer and forgot a swap.  

1-  Boot from the installer (don't panic) and make your way to the partionnner.

2-  You say you have 3 gigs free?  If they are part of another partition and you do not want to use all of it, select that partition and select it's size.  Enter a smaller number and make it go.  You just shrank that partition.
3-  make the free space into a swap space.  Make it go.  Stop the intallationafter that.

---

### Post by burnis on 2005-01-20
Just start cfdisk, set up a part of the free space to swap. After that, reboot the computer so it recognizes the partition change. (I don't know if you have to do this, but i think so)

Then run:
mkswap /dev/hdX

Add a swapline in /etc/fstab that looks like this:
/dev/hdX       none            sw          swap        0  0

---

