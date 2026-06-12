---
title: "HP pavilion dv6"
date: 2009-09-15
forum: Hardware
---

### Post by Lora Silva on 2009-09-15
Hello,

I've recently bought a HP pavilion dv6 1250sp, and I've installed the latest version of ubunutu 9.04, 64 bits. I've been having problems with the sound card - don't have any sound with videos, swf's, etc. 

I've tried using lspci -v, and the result I've obtained was 
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Hewlett-Packard Company Device 3628
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 80e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

I've also tried installing all sorts of decoders but with no success. Can anybody please help me...

Thanks :)

---

### Post by haxer on 2009-09-15
Install ALSA? :) . Becuse dv6 has 7.1 audio from scratch.

---

### Post by Lora Silva on 2009-09-15
Yes, got it installed but still have no sound :(

---

