---
title: "Ubuntu Installs but then does not boot after restart"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by nivarp on 2009-02-02
Hi,

I have a toshiba Portege 4010. I was running a previous version of ubuntu 8.04.1 and tried upgrading which hangs on splash screen after it rebooted, but boots and works fine on the previous kernel 2.16.20-16. So I stuck in a new hdd and installed the latest version of ubuntu 8.10 which installed fine, but when it reboots, it hangs again on the splash screen. Tried recovery mode and it hangs at:

[ 30.340268] cs: memory probe 0xa0000000-0xa0ffffff:

Anybody have an idea of what it could be. I did a memtest and that passed fine.

Thanks
nivarp

---

### Post by nivarp on 2009-02-02
> **julian5 said:**
> Try to install the GRUB again. if you still get the splash screen then try this,


Highlight Ubuntu title in boot Menu ( GRUB ) using up/down arrow keys and press e. Select kernel line and press e again. Delete quiet and splash words. Hit enter key and b.

Highlight Ubuntu title -- e --- select kernel line --- e --- delete quiet splash --- hit Enter key --- b.

I tried what you said and still get the same thing :(

---

### Post by icanfly0307 on 2009-02-02
How much RAM do you have? Have you tried waiting for a while to see if boots normally a few minutes later? I had the same problem except that I got a different message. I had to wait 4 minutes until the boot continued normally...

---

### Post by nivarp on 2009-02-02
> **icanfly0307 said:**
> How much RAM do you have? Have you tried waiting for a while to see if boots normally a few minutes later? I had the same problem except that I got a different message. I had to wait 4 minutes until the boot continued normally...

I've got 751mb of RAM installed. I've also left it for an hour or so to see if it boots, but it doesn't.

---

### Post by icanfly0307 on 2009-02-02
Do you have any types of external or internal flash cards? Maybe like SD or Sony MemoryStick Pro? They hang up the boot sometimes.

---

### Post by nivarp on 2009-02-02
> **icanfly0307 said:**
> Do you have any types of external or internal flash cards? Maybe like SD or Sony MemoryStick Pro? They hang up the boot sometimes.

Only card I had in there was a 3com 56k pcmcia modem, which I haven't used in years and completely forgot about. Took that out and it booted fine. I guess that was causing the problem. Thanks for the advise, I would never have thought of it!

Thanks
nivarp

---

### Post by icanfly0307 on 2009-02-02
Glad to know I could help. :D

---

