---
title: "How Come No Slutions - Where Are The Wizards ?"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by bdd4 on 2006-01-04
New ubuntu user:

My System: 1.5GHz Athlon,1GB ram,40GB HD, Netgear wireless network, HP Laserjet4 printer

PROBLEM: MY LASERJET4 PRINTER DOES NOT SHOW EITHER UNDER Smb4K or Windows2000.

I can print to the Laserjet4 printer from ubuntu.

With Smb4K I can see the Canon Pixma printer on the networked windows 2000 system. I can print to it from ubuntu.

With Smb4K I can see my ubuntu network but not the Laserjet 4 printer.
From the windows 2000 system I can see my ubuntu network but not the HP
Laserjet4.

I have set the Laserjet4 as LOCAL and NETWORK - can't see it.

I have done smbmnt -s parallel /dev/lp0 and smbmnt -s parallel /dev/Laserjet4.
No help.

Your suggestions please ?

---

### Post by earobinson on 2006-01-04
so you cant use the printer in linux or windows?

Could it just be broken (a hardware issure)

---

### Post by rjwood on 2006-01-04
Have you tried searching the forums using either your printer name or just 'printer'. The wizards have probably answered this question already---just seek and ye shall find...Good Luck!

---

### Post by bdd4 on 2006-01-04
i can prine from my ubuntu computer to my local hp laserjet4 printer.
i can print from my ubuntu computer to my networked win2k canon i6000d pixma printer.
i can't print from the win2k networked computer to the laserjet4 connected to the ubuntu computer.
all hardware is good.

---

### Post by bdd4 on 2006-01-04
i've searched networking probs and also some printer probs looking for linux drivers
for my canon i6000d pixma.

---

### Post by azteech on 2006-01-04
[quote=bdd4]New ubuntu user:

My System: 1.5GHz Athlon,1GB ram,40GB HD, Netgear wireless network, HP Laserjet4 printer

PROBLEM: MY LASERJET4 PRINTER DOES NOT SHOW EITHER UNDER Smb4K or Windows2000.

I can print to the Laserjet4 printer from ubuntu.

With Smb4K I can see the Canon Pixma printer on the networked windows 2000 system. I can print to it from ubuntu.

With Smb4K I can see my ubuntu network but not the Laserjet 4 printer.
From the windows 2000 system I can see my ubuntu network but not the HP
Laserjet4.

I have set the Laserjet4 as LOCAL and NETWORK - can't see it.

I have done smbmnt -s parallel /dev/lp0 and smbmnt -s parallel /dev/Laserjet4.
No help.

Your suggestions please ?[/quote]

IMHO, sounds like you may not have turned on the printer sharing option. See this thread for printer sharing [http://www.ubuntuforums.org/showthread.php?t=108211&highlight=printer+share](http://www.ubuntuforums.org/showthread.php?t=108211&highlight=printer+share)

---

### Post by ed_d on 2006-01-04
^^^Exactly where I was heading ^^^

---

