---
title: "freeze while booting on the Toshiba Satellite A60682"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by gix on 2005-06-06
sometimes my ubuntu box doesn't boot due to some strange (hw related I think...) reasons...

after grub start to load the kernel, the the screen is cleared and I can see only the first line saying:
**Starting Ubuntu...** 

... and nothing else!

so the only solution that I've found to work is to power off the system, detach the batteries and the AC adapter for a while (30 seconds about...).
After that I can switch on the system and successfully load ubuntu...

NOTE: if it could help, after the first line (cited above) I've always the following lines:
[B]
ide2: I/O resource 0x3EE-0x3EE not free
ide2: ports already in use, skipping probe
[/B]

I've also windows xp installed. no problems encountered while booting  with it.

Anybody here encountered the same/a similar problem?
Anybody could give me some hints?

Your frustrated
gigi

---

### Post by blind0wl on 2005-06-20
In your /boot/grub/menu.lst can you add a ```
ide=nodma
``` to the end of the main kernel line?

so something like:

```
kernel  /boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash **ide=nodma** 
```

---

