---
title: "Compaq Armada 1750 Issue : MBR rewritten by Ubuntu"
date: 2005-10-29
forum: Hardware &amp; Laptops
---

### Post by icekin on 2005-10-29
I have a compaq Armada 1750. This laptop uses a special Diagnostic partition to store its BIOS, the purpose of the actual ROM BIOS is to allow booting into this partition. In addition, I read that for this Diagnostic partition to function properly, the MBR must not be disturbed. Specifically, there is a 12h portion of the MBR that must be left alone.

By installing Ubuntu, if I choose to write Boot loader to MBR, will it overwrite this 12h portion? Will making a boot partition on the hard disk to store the boot loader get around this problem (meaning I won't have to touch the MBR).

My laptop will be running a Ubuntu + Windows XP Pro SP2.

---

### Post by icekin on 2005-10-31
Okay, after trying various different methods, I don't think that it is possible to have a working F10 key and a working bootloader at the same time. Even if I make a boot partition of 50 MB size and make it bootable and install GRUB to that, after the boot up, I get "cannot load OS" error. Thus, the boot loader must be installed on MBR, it seems. I read somewhere that I can edit some vmlinuz to get past this problem, but I don't know how to do that.

Once GRUB is written to MBR, you cannot enter the diagnostic tools by pressing F10 anymore, even though the white cursor will blink in the top corner. However, diagnostic tools can still be started by booting through a diagnostic tools floppy.

After installing GRUB to MBR, I tried deleting the diagnostic partition and recreating it, but I still was not able to enter through F10.

---

