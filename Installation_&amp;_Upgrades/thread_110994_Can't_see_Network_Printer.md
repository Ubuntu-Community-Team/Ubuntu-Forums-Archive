---
title: "Can't see Network Printer"
date: 2006-01-01
forum: Installation &amp; Upgrades
---

### Post by bdd4 on 2006-01-01
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

bdd4

---

### Post by bdd4 on 2006-01-04
IMHO, sounds like you may not have turned on the printer sharing option. See this thread for printer sharing [http://www.ubuntuforums.org/showthre...=printer+share](http://www.ubuntuforums.org/showthre...=printer+share)

EUREKA! - THIS WAS THE SOLUTION! - IT WORKS LIKE TEXTBOOK!

---

### Post by bdd4 on 2006-01-04
[QUOTE=bdd4]New ubuntu user:

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

bdd4[/QUOTE]

IMHO, sounds like you may not have turned on the printer sharing option. See this thread for printer sharing [http://www.ubuntuforums.org/showthre...=printer+share](http://www.ubuntuforums.org/showthre...=printer+share)

EUREKA! - THIS WAS THE SOLUTION! - IT WORKS LIKE TEXTBOOK!

---

