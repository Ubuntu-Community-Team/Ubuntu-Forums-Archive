---
title: "Inspiron 9300 with black screen :("
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by spencer_lai on 2005-12-23
I tried installing breezy onto my inspiron 9300 (Pentium m 740, ATI Radeon x300).  After asking for which type of installation i would like to run, it just gives me a black screen.  Actually not really there is some sort of weird line coming out for the screen and it goes from really dim to really visible.  I guess that's a fglrx driver issue so i try running the live 5.04 cd and the same problem occurs.

Any clue how to install Breezy onto my machine :(

---

### Post by wanger123 on 2005-12-23
Hi I have Breezy on Dell 9300 with no probs at all. Also using ATiX300. You could try typing linux vga = 771 at the boot prompt or use the noapic option. Try searching the forum
ciao
wanger

---

### Post by spencer_lai on 2005-12-24
I use the following parmameters and it works.
expert pci=noacpi vga=771

---

