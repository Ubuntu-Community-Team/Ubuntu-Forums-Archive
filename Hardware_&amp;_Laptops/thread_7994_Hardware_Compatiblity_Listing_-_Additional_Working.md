---
title: "Hardware Compatiblity Listing - Additional Working Hardware"
date: 2004-12-13
forum: Hardware &amp; Laptops
---

### Post by unixpenguin2004 on 2004-12-13
Hello Ubuntu Linux Community!  Last night I downloaded and installed Ubuntu with a plethora of extra programs and libraries.  I tried Ubuntu out on my custom system, which is a Shuttle AN-35 Ultra motherboard, AMD Athlon XP 2500+, 256MB PC2700 DDR, 40GB IBM IDE, 2MB Matrox Millenium PCI, nForce2 Chipset (IDE, USB, AGP).

After just 3 hours of use I haven't had one problem.  All of my hardware works out of the box flawlessly.  Every program installed works without a hitch (Except Xmms).

If you didn't know... XMMS needs the LMikMod2 Library to operate.  When I've installed XMMS using apt in the past I have to install libmikmod2 additionally.  If you can contact the Debian team and get the dependency integrated with XMMS' package.

Anyways thank you for providing such a great product.  It's fast, easy, stable, and free.  I will be installing Ubuntu on my mother's computer which currently runs Debian (Sarge) in a few hours.  I hope to continue participation in every aspect I can for this project.

---

### Post by word_virus on 2004-12-13
>XMMS needs the LMikMod2 Library to operate. When I've installed XMMS using apt in
 >the past I have to install libmikmod2 additionally. If you can contact the Debian team 
>and get the dependency integrated with XMMS' package.

As I understand it from another forum post the LMikMod2 lib is essential to the operation of XMMS only if you have an NVIDIA graphics card.

I installed XMMS w/o the library (I have an ATI card) and XMMS worked just fine, tho the xterm I launched it from did complain that it couldn't find libmikmod2.o, so I don't know that it counts as a dependency since it's only necessary for certain hardware?

---

