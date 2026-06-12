---
title: "SP5100 TCO timer error"
date: 2011-11-04
forum: Hardware
---

### Post by MarcosDurrant on 2011-11-04
Ever since I upgraded to 11.10 I have been having some quirky issues with my desktop.  First the WIFI would show that it was connected but then not go anywhere.  The way around this was to just go with a straight Ethernet connection and then I was able to update and it seems to work.  Now the issue is that when I attempt to boot I get: "SP5100 TCO timer: mmio address ..... already in use" and it hangs.  Once it hangs I hit get to a terminal and uname -r gives me 3.0.0-12-generic and grep -i sp5100 /boot/config-`uname -r` gives me CONFIG_SP5100_TCO=m.  Is it possible to just disable this driver (SP5100) from a bash prompt?  Any help would be greatly appreciated.

---

### Post by MarcosDurrant on 2011-11-05
Bump.

---

### Post by bcschmerker on 2011-12-16
I can confirm this on 10.04.4-LTS with Kernel 3.0.0.14 (package: linux-image-generic-pae-lts-backport-oneiric); during boot, the Kernel reports "shpchp...: Cannot reserve MMIO region" and "TCO timer...:  MMIO address 0xfec000f0 already in use."  No kernel panic, fortunately for me.  I've yet to figure out whether I can remap some of the devices reported as conflicting on my hybrid Everex'® Gigabyte® MA78GM-S2HP in the Phoenix® Award® BIOS Settings.

---

### Post by ivotedforkodos on 2012-01-14
> **bcschmerker said:**
> I can confirm this on 10.04.4-LTS with Kernel 3.0.0.14 (package: linux-image-generic-pae-lts-backport-oneiric); during boot, the Kernel reports "shpchp...: Cannot reserve MMIO region" and "TCO timer...:  MMIO address 0xfec000f0 already in use."  No kernel panic, fortunately for me.  I've yet to figure out whether I can remap some of the devices reported as conflicting on my hybrid Everex'® Gigabyte® MA78GM-S2HP in the Phoenix® Award® BIOS Settings.

Does anyone know how to solve this!! I installed 11.10 and now I can't boot!! The booting process hangs with:
SP5100 TCO timer: mmio address 0xb8fe00 already in use

---

### Post by luissil on 2012-06-18
> **ivotedforkodos said:**
> Does anyone know how to solve this!! I installed 11.10 and now I can't boot!! The booting process hangs with:
SP5100 TCO timer: mmio address 0xb8fe00 already in use

I have the same problem but with 12.04, I think the problem begins after a kernel update... 

First, system reboot, then can't boot and mmio error appears...

---

