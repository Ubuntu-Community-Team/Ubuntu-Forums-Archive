---
title: "Problem with ice1724 card"
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by park on 2006-04-16
The problem I'm encountering is that my sound card driver loads incorrectly.  dmesg gives me only one line of error that is remotely related:

[   52.149437] ice1724: Using board model Chaintech AV-710
[   52.152300] ice1724: Invalid EEPROM version 1

The "Using board" line only shows up because I've added the line 
options snd-ice1724 model=av710
to /etc/modprobe.d/alsa-base
The only other kernel change I've made is adding the flag "pci=noacpi" to grub.  It is unclear if this matters.  I didn't find any similar errors via google, including in the LKML, so I'm at a bit of a loss.

My complete dmesg follows.

---

### Post by park on 2006-04-16
Update:
The sound card works fine.  I've issued 12 demerits to myself.

The primary reason this appeared as a problem was that the order of detected sound cards in my system changed.  The AV710 is now card 2, instead of 1.  For those who care about such details:
In the Breezy kernel
0 = onboard NFORCE
1 = AV-710
2 = Bt87x

Now, /proc/asonud/cards contains:
0 [CK804          ]: NFORCE - NVidia CK804
                     NVidia CK804 with ALC850 at 0xfe02d000, irq 5
1 [Bt878          ]: Bt87x - Brooktree Bt878
                     Brooktree Bt878 at 0xfdffe000, irq 10
2 [AV710          ]: ICE1724 - Chaintech AV-710
                     Chaintech AV-710 at 0xcc00, irq 7

---

### Post by spm on 2006-04-21
Good info...

I am also on Breezy 5.10 Ubuntu with the same card..

My card does not seem to be detected...How did you get it detected???

Ubuntu seems to only detect the Via motherboard sound...which I dont want...

any hints/tips?

Thanks!

---

### Post by park on 2006-04-21
Unfortunately I doubt I can help.  I had no trouble getting it detected.  You can always try the old "modprobe ice1724" and look at the tail of dmesg to see if there is some useful error message.

Good luck!

---

### Post by spm on 2006-04-22
I feel like an idiot! Thank you!

That seemed to do it, module loaded anyways...btw it was modprobe snd-ice1724, in case anyone follows.

Now lets see if sound comes out of there...

---

