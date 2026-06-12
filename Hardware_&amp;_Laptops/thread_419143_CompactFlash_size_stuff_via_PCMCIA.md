---
title: "CompactFlash size stuff via PCMCIA"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by fredsea on 2007-04-22
I had this great idea to use my (essentially unused) PC Card slot to access a CompactFlash sized 4G "Photo Hard Drive" by Seagate. I got a PC Card adapter, and when I plugged it in, dmesg told me that a PC Card had been inserted in slot 0 - but that was it, and I could find no way to mount, or otherwise check on the disk... :confused:

Using the PC Card slot for an old CompactFlash drive (flash memory, that is) was unsuccessful too, but here the message was 
[17184683.392000] hde: drive not ready for command
[17184683.440000] ide2: reset: success
[17184683.440000] hde: status error: status=0x20 { DeviceFault }
[17184683.440000] ide: failed opcode was: unknown
[17184683.440000] hde: drive not ready for command
[17184683.488000] ide2: reset: success
[17184683.488000] hde: status error: status=0x20 { DeviceFault }
[17184683.488000] ide: failed opcode was: unknown
[17184683.488000] end_request: I/O error, dev hde, sector 0
[17184683.488000] hde: drive not ready for command

and, when trying to mount hde nonetheless,

mount: /dev/hde: can't read superblock

I am mentioning this last attempt, just to say what happened in another attempt. It may be something with my PCMCIA controller, for all I know (the laptop is a not-so-new-anymore Sharp MM20, with the efficeon Transmeta chip - Ubuntu works great for everything else). I don't need the flash drive, but I would love to use the HD. I am not sure what output would be useful to diagnose the problem.

Thanks!!

---

