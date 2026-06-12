---
title: "Trouble with the partitioner"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by dorado29 on 2009-02-16
Hey so im trying to install ubuntu onto my computer. It runs fine from the disc but when i try to install it my hard drive doesnt show up in the partitioning step. What do you think could be causing this? Step 4 of installing ubuntu is just completely blank, perhaps i installed my hard drive incorrectly when i built the computer?

---

### Post by Pumalite on 2009-02-16
Check your cables; for sure. Also jumpers.
If you can boot your Live CD; post:
```
dmesg
```

---

### Post by dorado29 on 2009-02-16
Weird.. The hard drive is connected via sata cable then plugged into the mobo in what i think is sata port one or two. Its a p5q asus board. Is there a way to check if its plugged in via bios?

---

### Post by caljohnsmith on 2009-02-16
So your HDD is SATA? If so, does your BIOS have "AHCI" available for your HDD? If it does, how about enabling AHCI for the HDD, then boot the Ubuntu CD again, but this time press F6 for boot options, and at the end of the line it shows add:
```
pci=nomsi
```
Then try booting with the "try Ubuntu without making changes option". Let me know if that works or not.

---

### Post by dorado29 on 2009-02-16
how do i get to that in bios? i looked through a bunch of the menus and didnt find anything about hard drives or memory or AHCI

to clear things up for anyone else, im trying to figure out if my HDD is even connected properly because if it's not then that explains the partitioning issue in ubuntu installer

---

### Post by caljohnsmith on 2009-02-16
I don't know, because BIOS settings vary greatly from motherboard to motherboard, and also depending on which BIOS version you are using. You could check the manufacturer's website of your motherboard if you need help with it.

---

### Post by dorado29 on 2009-02-16
okay i picked a random sata port and plugged the HDD sata cable into it so now ubuntu recognizes it. its all installed and whatnot now i just have to get it on my wireless network. i installed a dynex PCI card yesterday. how can i get this desktop onto my wireless now? im guessing dynex isnt supported by ubuntu lol

---

