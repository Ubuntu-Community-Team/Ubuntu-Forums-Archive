---
title: "Disabling Managed Boot  Agent"
date: 2009-02-08
forum: Installation &amp; Upgrades
---

### Post by mightyQ on 2009-02-08
I am trying to replace xp on my dell inspiron 2600 with ubuntu.
It appeared to install ok (although in default graphics mode, I can clean that up later I guess), and I can boot into it from the 8.10 installation CD.
But when I try to boot normally after the install, Managed Boot Agent (MBA) V4.30 (BIOS Integrated) starts up. It fails to find a network boot server, and then reports Operating System Not Found. 
I can get into MBA to configure it, but all of the selectable boot options are network boots.
My question is, does this really mean there is no OS found, or does the MBA somehow not go to the next bootable source? 
I have never run into MBA before, and don't know why it shows up at all. 
I will try a re-install, but if that does not work I don't know how to disable the MBA.

Any advice would be appreciated

---

### Post by mightyQ on 2009-02-08
OK, I have resolved this particular issue by updating the BIOS from A03 to A08.
Maybe just the action of reflashing did the trick, but I am not tempted to go back to A03 at this point.

---

