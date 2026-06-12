---
title: "&quot;dissconnect&quot; a swap partition and start using a swap file"
date: 2008-11-20
forum: General Help
---

### Post by b166er on 2008-11-20
Hi
I recently installed Ubuntu on a machine and choose to add a swap partition on the local hdd, (the same HD I boot from).

But now this machine has an extremly fast hardware-Raid connected to it, (fiber connection and everything). And I wanna try having all my swap on this Raid.

So how do I make linux forget about the Swap partition and only use a certain Swap file (or partition) that resides on this raid?


And does anyone know of another method of making ubuntu faste if there is a raid like this in the picture?

---

### Post by philinux on 2008-11-20
How much ram have you got. I've got 2 gigs and swap is never used at all.

---

### Post by b166er on 2008-11-20
4 gig.

But I work with Professional video effects.
And this computer will do allot of uncompressed 1080p effects.
this means very heavy computing usage.

The applications that does stuff like this use up allot of ram to sore these heavy files. 

you actually need to have a super raid to be able to play these files in realtime.

---

### Post by ilrudie on 2008-11-20
Create the swap file with *mkswap* and enable it with *swapon*.  Then disable your existing swap partition with *swapoff*.  If every thing still works to your liking change */etc/fstab* to reflect the use of your shiny new swap file and remove the old swap partition if you don't want to use it anymore.  Reboot to make sure your swapfile comes up.  Use *top* or *free* to check.  Check the man pages for the commands to get all the correct flags.

---

### Post by b166er on 2008-11-20
Oh thanks.
I didn't know that you could point fstab to a file.

---

### Post by philinux on 2008-11-20
> **b166er said:**
> 4 gig.

But I work with Professional video effects.
And this computer will do allot of uncompressed 1080p effects.
this means very heavy computing usage.

The applications that does stuff like this use up allot of ram to sore these heavy files. 

you actually need to have a super raid to be able to play these files in realtime.

Very heavy stuff. :)

---

