---
title: "Homebrew Desktop 32 bit to 64 bit upgrade"
date: 2010-01-04
forum: Hardware
---

### Post by momist on 2010-01-04
Hi there.  Can someone please give me some advice on my hardware upgrade?

I'm currently running plain vanilla Karmic Koala Ubuntu 9.10 on a 32 bit single core AMD processor, with AGP video card and PCI boards for various things.  1GB is my maximum permitted memory.  I have two IDE hard drives and one IDE optical drive.  My '/home' is on a separate partition, as are my music, images, videos and documents, although some stuff is inevitably in the /home directory as well.  There's not much in root except what belongs there.

I've bought a used Asus A8V Deluxe motherboard which will support these other hardware items, but permit 2GB DDR400 matched dual memory and an Athlon64 X2 dual core processor.  It will also support SATA and RAID for future further upgrades, I hope to replace the hard drives in 2010 sometime, and increase the memory to 4GB.  So how do I go about preparing for the upgrade please?  

I am kind of hoping that I can simply plug in all the bits and switch on - and faithful Ubuntu might detect the new hardware and "just work".  However, I suspect I might have to re-install some or all of the applications to achieve 64 bit operation.  Will the current kernel simply switch itself, or need telling to switch, or need an upgrade?

Thanks for any advice, or insights.  The upgrade should come in at about  £100(UK).  I do hope it ends up a bit quicker  ;)

---

### Post by Cheesemill on 2010-01-04
Your new system should work just fine by plugging the old drives in, no reconfiguration needed.

But....

It will still be running 32-bit Ubuntu as that is what is installed on your drive.
There is no upgrade path from 32-bit to 64-bit, to get 64-bit Ubuntu on the machine you will need to do a clean install. As you have /home on a separate partition then you won't lose any of your data/settings but you will have to re-install any applications you have that aren't present in a default install.

---

### Post by momist on 2010-01-04
> **Cheesemill said:**
> Your new system should work just fine by plugging the old drives in, no reconfiguration needed.


Thanks Cheesemill, that is what I was hoping.


> **Cheesemill said:**
> 
It will still be running 32-bit Ubuntu as that is what is installed on your drive.

I guessed as much.  I could of course wait for 10.04, or simply get the 64 bit version of 9.10

I noticed that if I go to the "Get Ubuntu" site, it only offers me the 32-bit version.  I suspect that this is because something clever is detecting my processor and directing me accordingly.  I tried looking for the 64-bit version to download ready (in case something is broken after the re-build) but can't easily find it.  I'll try again when I've more time.

Cheers for the encouragement!
Ian

---

### Post by Cheesemill on 2010-01-04
On the download page just click 'Alternative download options' under the big green button and you can select 64-bit (although you should really use torrents if possible to keep the load off the Canonical servers).

---

