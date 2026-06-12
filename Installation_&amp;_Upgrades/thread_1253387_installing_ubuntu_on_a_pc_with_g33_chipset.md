---
title: "installing ubuntu on a pc with g33 chipset"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by manusha on 2009-08-30
hi,
im trying to install ubuntu 9 desktop on a pc with intell g33 chipset. During installation i encounter three problems which may be connected.
1) CD reading is extremely slow. (the writing speed of the CD was 12X and works fine with the same CD-ROM with windows)
2) x-server fails to start when i try to boot from live CD.
3) when i try to install it, it hangs.

Could any one guess the problem? 
the mother board brand is FoxConn.

Thank You

---

### Post by manusha on 2009-08-30
I found the problem. In BIOS setting there is an option to set the size of the VGA buffer. It was set to 1MB. I changed it to 8MB. Now everything works great.

---

