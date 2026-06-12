---
title: "OpenBIOS. Anyone used it?"
date: 2009-10-16
forum: Hardware
---

### Post by ElevenWarrior on 2009-10-16
anyone heard of it? [http://www.openfirmware.info/OpenBIOS](http://www.openfirmware.info/OpenBIOS)
I came across it looking for ways to make linux faster, I have never flashed my BIOS before, so I'm wondering excalty what this does.
Anyone have any ideas or tips?
thanks in advance.

---

### Post by Giblet5 on 2009-10-16
Before you even think of flashing a 3rd-party bios, you should grab a new flash chip and install it. THEN burn to it.

That will keep you from bricking your motherboard; if the OpenBIOS bricks your board, you can just put the old flash back in and re-setup the CMOS config.

Haven't tried it.

Wouldn't try it.

And I've designed motherboards.

---

### Post by Dark_Stang on 2009-10-16
> OpenBIOS can be used directly as a boot ROM for QEMU system emulators for PPC, PPC64 and Sparc32. OpenBIOS/Sparc64 also exists but does not work very well yet. OpenBIOS/Sparc32 can boot Linux, NetBSD and OpenBSD.
Looks like it isn't designed for todays x86 and AMD64 based machines any.

Edit: And as the poster above me said, I would never install cracked firmware on a motherboard of a computer.

---

### Post by ElevenWarrior on 2009-10-16
okay, thanks for your advice. Dosen't really seem worth the risk.

---

### Post by falconindy on 2009-10-16
I'd love to be able to use OpenBIOS or Coreboot if not for their (expectedly) poor support of motherboards. Coreboot in particular is really neat -- you can load part of GRUB directly into it to make booting extra quick. People report 5 seconds to a shell login.

---

