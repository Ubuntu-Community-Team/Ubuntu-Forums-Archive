---
title: "Can Intrepid and Vista Home Basic CoExist peacefully?"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by kystorms on 2008-12-17
My kids just got a new computer from their grandparents, my oldest work in  graphics on line  ( videos etc) and really needed a windows machine to work on as well as their Ubu machine.

I am wondering, can I take their present Intrepid hard drive from its current home in one case, and place inside case alongside the HD that has Vista Home basic on it? And if I can, will it run and  HOW to do this?

Pardon this mom for not being as solid on this topic as I should be and many thanks in advance for any and all help!

---

### Post by mrbiggbrain on 2008-12-17
> **kystorms said:**
> My kids just got a new computer from their grandparents, my oldest work in  graphics on line  ( videos etc) and really needed a windows machine to work on as well as their Ubu machine.

I am wondering, can I take their present Intrepid hard drive from its current home in one case, and place inside case alongside the HD that has Vista Home basic on it? And if I can, will it run and  HOW to do this?

Pardon this mom for not being as solid on this topic as I should be and many thanks in advance for any and all help!

i dont know the exact answer, but i belive yes you could have listas boot loadet "NTLDR" point to the grub on the second HDD and boot, i belive :-/

---

### Post by logos34 on 2008-12-17
> **mrbiggbrain said:**
> i dont know the exact answer, but i belive yes you could have listas boot loadet "NTLDR" point to the grub on the second HDD and boot, i belive :-/

that's one way to do it, but it's easier to use ubuntu grub to dual boot--provided you can get linux to boot on your machine.  Try it and if it works (and the hardware differences bewtween the two machines may prevent it) post back from inside ubuntu.  You'd just need to add a windows entry to menu.lst

go into the bios at startup and select ubuntu as the boot disk

---

