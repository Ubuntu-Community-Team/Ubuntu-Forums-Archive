---
title: "Hardy to Intrepid causes problem with console fonts"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by DaleAmon on 2009-03-19
I upgraded Hardy to Intrepid last night on a very old but very stable and important server and found that it now gives me boot and console fonts in an un-usably large print.

I have tried many vga values and the results seem to fall into 3 categories:

1) The large font appears
2) Randomly placed green squares of about the same character size appear.
3) I get a black screen.

The case of 1 seems to happen for all the vga modes I have tried that are specified like 80x20 and such. The case 2 happened in all of the 0x3nn vga modes I tested; pretty much everything else gives me a black screen (769, 773, 792 and many others).

I've spent the better part of an afternoon trying to get this working again as I do often use this machine as a plain glass tty. It is at present unusable in that capacity. It does work fine for ssh and X... but I never use it in X because it is too underpowered for anything except the file server ops for which it has served well and reliably for about 9 years.

I am suspicious that the problem is a switch to a frame buffer. The monitor itself works fine with another Intrepid machine on the same KVM.

---

