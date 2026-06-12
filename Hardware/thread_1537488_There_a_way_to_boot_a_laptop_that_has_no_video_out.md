---
title: "There a way to boot a laptop that has no video output and connect via network or USB?"
date: 2010-07-23
forum: Hardware
---

### Post by MechaMechanism on 2010-07-23
My Dell laptop with 15 screen has fried the video output.  It's not economical to replace video output.  The rest of the computer works perfectly.  I would like to know how to boot into a headless environment.  I would like to repurpose the laptop as a headless server.  How can I do it.  It has USB, Ethernet, Firewire.

---

### Post by Joe of loath on 2010-07-23
You would have to remaster a live-CD to run ssh on boot, so you can SSH in and install.

Alternatively, you can install with the HDD in another PC, and set everything up on that. This would be easier, but less fun.

---

### Post by MechaMechanism on 2010-07-23
> **Joe of loath said:**
> You would have to remaster a live-CD to run ssh on boot, so you can SSH in and install.

Alternatively, you can install with the HDD in another PC, and set everything up on that. This would be easier, but less fun.
I guess it's remastering time then.  I think I'll keep both laptops off the internet while setting up the headless server.

---

