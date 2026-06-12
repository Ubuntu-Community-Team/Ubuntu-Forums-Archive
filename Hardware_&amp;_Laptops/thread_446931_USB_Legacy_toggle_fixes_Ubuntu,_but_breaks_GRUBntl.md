---
title: "USB Legacy toggle fixes Ubuntu, but breaks GRUB/ntldr"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by ledneh on 2007-05-17
For some time now I've been trying to install Feisty Fawn. My problem has been that my USB keyboard (a Logitech G15) would eventually lock up with no logged indication of the cause. It would either no longer respond, or repeat the last key pressed forever (even when the keyboard is unplugged!).

Somewhere I found that turning off USB Legacy support in the BIOS would fix this. While that DID fix it, it caused the problem that ntldr, GRUB, and probably LILO no longer recognize the keyboard. Which makes sense, I guess; with legacy support off, once POST is complete the system needs to load a driver to keep using the keyboard.

The problem here is that either way I go, I'm screwed. If I leave legacy support on I can't use Ubuntu for more than fifteen minutes or so before the keyboard locks; and if I turn it off I can't navigate any boot loaders, which is a pain in the *** all its own.

So how do I reconcile this problem? How do I fix it so that I can still keyboard through boot loaders while having full access to Ubuntu?

Thanks!

(and no, "get a PS/2 keyboard" is NOT a solution ;))

---

