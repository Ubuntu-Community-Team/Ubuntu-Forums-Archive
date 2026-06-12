---
title: "Sony Vaio circa 2001"
date: 2008-03-04
forum: Hardware &amp; Laptops
---

### Post by Nitro Fan on 2008-03-04
Following my example! one of my collegues has now decided to take the plunge into Linux he has a Sony Vaio circa 2001 and is planning to install Xubuntu (currently downloading it) are there any known issues with Vaio machines and Xubuntu?

---

### Post by lloyd_b on 2008-03-04
> **Nitro Fan said:**
> Following my example! one of my collegues has now decided to take the plunge into Linux he has a Sony Vaio circa 2001 and is planning to install Xubuntu (currently downloading it) are there any known issues with Vaio machines and Xubuntu?

My main work machine is a Vaio PCG-F450, from around 2000, running Xubuntu.  The only real headache I've had with it is the fact that the USB->Ethernet device built into the port replicator isn't entirely stable for me (the networking tends to lock up every once in a while), but that's easily avoided if he's using a PCMCIA ethernet card (which is pretty much necessary anyway, as that USB Ethernet device is only 10Mb).

One note: If he has less than 256Mb of memory, then use the "Alternate" install CD - the "Live CD" probably won't work.

Lloyd B.

---

### Post by Nitro Fan on 2008-03-04
Hi lloyd_b

Thanks for the reply he will be running it wireless at home so I hope it should be OK fingers crossed.

---

### Post by ubonetu on 2008-03-04
You may have the same Via sound card as I do on my pcg-fxa36.  The input is exclusively MONO.  It's really irritating.  I've found some other distros that support my M-Audio Micro usb sound input device but as of yet, not Ubuntu.  If there is a way to activate usb-audio maybe ```
modprobe snd-usb-audio
``` (just thought of that) please let me know.  I'll re-post if I get it to work.  And sorry for the confusing post.

Thanks

---

