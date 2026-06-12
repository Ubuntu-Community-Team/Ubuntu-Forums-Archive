---
title: "xorg/kde &quot;broken&quot; after updates"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by Tx1491 on 2009-04-30
Hi, a friend of mine who uses ubuntu just did some updates this morning and now he's stuck with CLI.

The kubuntu (it's ubuntu with the kubuntu themes/etc installed) splash screen thing comes up, the progress bar gets to about 90% then it throws him back to the terminal at a login prompt. No useful error messages or anything are showm.

He's using 9.04 (rusty marmoset or whatever stupid name they gave it) and updates regularly so whatever broke his system was included in the last couple days worth of updates.

Anyone else had this? or any idea where to start diagnosing it? (I'm fine with sane linux distros but ubuntu does so much stuff differently I don't know where to start).

Any help, tips, pointers, etc would be much appreciated.

PS, the last set of updates installed a load of kde4 apps, so maybe the latest updates replace the whole kde3.5 system with kde4 (I hope not)

---

### Post by emarkay on 2009-04-30
What kind of machine, what graphic card, and was it a new install or an upgrade?

---

### Post by Tx1491 on 2009-04-30
It's an Fujitsu Siemens AMILO Pi 1505 laptop with integrated Intel GMA950 graphics. The 9.04 system was upgraded from 1 or 2 versions back

I tried to get him to start kdm manually and it says kdmrc is missing, which is probably the cause but it turns out the network doesn't work in the terminal either so can't reinstall kdm to get that file.

Any idea where the wireless network settings are under /etc? It's not any of the files I'm used to in other distros and grep didn't help find the file either.

I think if I get the network working and reinstall kdm it might go.

edit: all working now. plugged in an eth cable, did apt-get update, upgrade and install kdm now everything works fine (well, as fine as it can be with trashy kde4)

---

