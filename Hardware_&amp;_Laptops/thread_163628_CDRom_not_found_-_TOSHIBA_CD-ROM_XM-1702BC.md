---
title: "CDRom not found - TOSHIBA CD-ROM XM-1702BC"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by Sophont on 2006-04-21
Hi,

I want to install Ubuntu on an old Laptop (Compaq Presario 1230, 96 MB).

I tried this with every version of Ubuntu since Warty.
I'm trying Dapper Drake Flight 6 while I write this.

The problem is the CDRom drive. Install starts fine but then waits minutes at 86% when detecting hardware while trying to find a cdrom driver.
After it fails I select "cdrom" manually from the list.

That sort of works - but takes 3-4 **days**. I'm not joking or exaggerating.

While reseraching this I found out that the stupid old thing is blacklisted in the kernel:
```

kernel-source-2.6.4 (2.6.4-1) unstable; urgency=low
+
+  * New upstream release (closes: #234631, #234754, #236570).
+  * Added vmlinux.syms:
+    . scripts/Makefile.modpost
+    . scripts/modpost.c
+  * Allow X86_MCE_NONFATAL to be a module:
+    . arch/i386/Kconfig
+    . arch/i386/kernel/cpu/mcheck/mce.c (Andrew Morton)
+  * **Black listed "TOSHIBA CD-ROM XM-1702BC"** in drivers/ide/ide-dma.c.

```

Don't know exactly what that means - but it doesn't sound helpful. ;-)

I'm letting it (DD Flight 6 - as server setup) run now for the 3-4 days it usualy takes - but if there is a problem later and I have to restart to change an option I might have to start all over again.

Any help for a workaround would be appreciated.

I'm looking into a network install as an alternative for the install, but it would be nice to make the cdrom usable.

More details about the hardware:
[LIST]
[*]Cyrix MediaGXtm MMXtm Enhanced
[*]32.0MB RAM (I put in an extra 64 MB)
[*]Toshiba CD-ROM XM-1702BC
[*]Generic IDE disk type01
[*]Generic NEC floppy disk
[*]NeoMagic MagicGraph 128ZV+ display adapter
[*]Standard 101/102-Key or Microsoft Natural Keyboard
[*]Compaq Presario 5K-DF WinModem
[*]Laptop display panel 800x600
[*]PS/2 Compatible mouse port
[*]XpressAUDIO(TM) 16-bit Sound
[/LIST]

---

