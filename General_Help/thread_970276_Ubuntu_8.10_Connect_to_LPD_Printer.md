---
title: "Ubuntu 8.10 Connect to LPD Printer"
date: 2008-11-04
forum: General Help
---

### Post by claytronic on 2008-11-04
Last night I needed to print something and realized I hadn't setup a printer my newly installed Ubuntu 8.10 laptop. Previous Ubuntu versions just worked when I needed to add a LPD print device. The new "Printer configuration" UI left me somewhat puzzled. Gone are well described UI options for LPD or IPP network printers. What happened guys? ;)

For those needing to print to an LPD network printer here's a quick and dirty HOWTO.


Open the Printer configuration utility
*System > Administration > Printing*

Click "New"

Select "Other" under Devices and enter the LPD
*lpd://<hostname or ip>/<device queue>*

*Example = lpd://192.168.100.10/LaserJet-5MP*

Continue on with the rest of the new printer wizard selecting the proper drivers for your device.

---

### Post by crosslink on 2008-11-22
Thanks claytronic, this was just what I was looking for.

I've successfully added TCP/IP printers in previous versions. This "add printer" dialog box didn't give me the cues I needed to figure out what form the URI needed to take.

---

### Post by brunojng on 2009-01-29
Many thanks claytronic!

I'm new to ubuntu and linux (as my main OS), and I was having some problems with the network printer configuration... I searched allot and only with your precious help I was able to print something!

Still, I have one question. By coincidence the printer I was trying to configure is a HP Laserjet 5M, so I really used your example (with my printer's IP). What can I do if I want to find out what is the queue of another printer?

Thanks!

---

