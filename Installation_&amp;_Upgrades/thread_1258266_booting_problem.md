---
title: "booting problem"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by pappy09 on 2009-09-04
After installing version 9.04 desktop edition and hitting the restart button it took me to where I had to choose Windows xp or Ubuntu, I chose Ubuntu then it said 10APIC resources could not be allocated loading please wait. next line was INITRAMFS _ flashing. I just dont know what to type in to move it along, any help would be appreciated. thanx:confused:

---

### Post by ronparent on 2009-09-04
This must be the epdemic or today. The very likely cause is incompatible apic/lapic support. Try running the live cd. Hit F6 in the menu after the language selection screen and spacebar to X out the apic and/or lapic support. If that works, add the noapic/nolapic options to your boot lines in menu.lst. There are other causes but it was a fix for me on three computers that would freeze in 9.04!

---

