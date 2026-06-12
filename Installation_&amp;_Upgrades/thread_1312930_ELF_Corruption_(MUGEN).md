---
title: "ELF Corruption (MUGEN)"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by shaffer.david on 2009-11-03
For me, upgrading to Ubuntu 9.10 cause some binaries to be "corrupted".  You need to do a "upx -d" on them to get them to work with the 2.6.31 kernel.

mugen$ file mugen
mugen: ELF 32-bit LSB executable, Intel 80386, version 1, statically linked, corrupted section header size
mugen$ ./mugen
Killed

[ the file will not execute until you use "upx -d" ]

# apt-get install upx


My kids love MUGEN, especially the SailorMoon chars.. anyway, I had to have that fixed.

---

