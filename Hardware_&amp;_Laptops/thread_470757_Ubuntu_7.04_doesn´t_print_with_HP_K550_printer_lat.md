---
title: "Ubuntu 7.04 doesn´t print with HP K550 printer latest firmware"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by Joaquin Negrete on 2007-06-11
I need help in order to print files in my HP K550dtn printer. I upgraded it to the latest firmware (SPP0013H). After this upgrade I cannot print files (.doc, pdf, test print pages) except Power Point files (using OpenOffice). When the printer receives the file, the power light button starts blinking and remains in that state permanently. So, in order to print the file I have to press the resume button once for every page I print (with this action the printer takes the sheet of paper and then prints). Because I usually use the duplex unit (automatic two-sided printing), I need to press twice the resume button in this two-step process for every page I print (one for one-sided printing and then another one for the other side printing). I have tested the HPLIB driver, version 1.7.4a ( hplip.sourceforge.net) and HPIJS driver (Ubuntu 7.04 driver). Also, I have tested the printing procedure in a Windows computer and it does not have this problem at all.

Could you help me with this technical issue? :o

---

### Post by timcredible on 2007-06-11
you may want to uninstall all your hplip stuff via synaptic, then install the latest hplip from hp (there's a nice ubuntu installer).

---

### Post by Joaquin Negrete on 2007-06-11
Than you very much timcrdible. I am using the latest hplip from hplip.sourceforge.net. There is not an official hplip from HP, so the only site where you can get it is from sourceforge. This problem didn´t exist with the original firmware (version A). Version H improves this: 

 Fixes 

# tray lock setting in Embedded Web Server (EWS) reset after printer power cycle
# HP Jetdirect en3700 Fast Ethernet external print server disconnection after hours of inactivity

 Enhancements 

# Reduce occurrences of paper jam, skew printing and paper dent.
# New printhead servicing algorithm to enhanced the black printhead health.
		
This problem doesn´t exit with Windows operating system. I have asked HP technical department but they don´t want to know anything about Linux, even though K550 is presented as a 100% Linux compatible. ¿? :)

---

