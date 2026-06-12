---
title: "is dual booting on pen drives possible?"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by c/Kr3t on 2009-06-07
i've got both ubuntu and backtrack 3 on my pen drive but when i boot into it, it just boots to the most recent one installed (bt3). is there any way to setup dual booting on pen drives?

---

### Post by Mighty_Joe on 2009-06-08
Does Backtrack 3 use Grub for a bootloader?  If it does, it should be as easy as adding an entry to the menu for your Ubuntu partition.  [Grub documentation here]("http://www.gnu.org/software/grub/manual/html_node/index.html")
If Backtrack has overwritten Grub, you should be able to re-install it onto your pen drive and create entries for both OS's.  Again, see the documentation linked above.

---

