---
title: "Epson EPL-6200L - Does not print!"
date: 2005-05-06
forum: Hardware &amp; Laptops
---

### Post by papdoc on 2005-05-06
I installed Ubuntu yesterday. My experience with Linux is virtually none... But the installation was uneventfull and everything works except my printer. 
The Epson EPL-6200L is recognized, it is listed under the "Printing" panel with the "Ready" sign under it, but I can not print anything!
Any ideas?
PS. Sorry for my English... :roll:

---

### Post by David Haas on 2005-05-08
Papdoc--Having the printer recognized does not mean it is set up to print. Fortunately, your printer, the Epson EPL-6200L, has its driver (PPD file actually) installed in Ubuntu. Before selecting this in the printer GUI (System>Administration>Printing, beginning in the top Ubuntu bar), you should make sure that all the "cupsys" and "foomatic" packages are installed by checking this out in Synaptic package manager: System>Administration>Synaptic package manager. When they are installed--they probably already are--work in the printer GUI, as noted above, to select your printer under the "driver" heading and then click "install driver." Here you must click through the files menu to reach the PPD file for your printer. It's directory path is /usr/share/cups/model/foomatic-ppds. In the foomatic-ppds directory, you'll see the PPD file for your printer: Epson-EPL-6200L-epl6200l.ppd.gz. Selecting this by clicking "open" will decompress the file and make it operative. Well, let us know how it goes.
David

---

### Post by accord on 2007-01-19
Hi. I've just installed dapper, and I'm having the same situation as the original poster. Print jobs have status "Paused" (or something equivalent, because it's in Chinese) and trying to resume the printer does nothing. I tried the advice given above, now the driver pane says "Default (CUPS)". After a print job is sent, it shows up briefly in the pending jobs (around 5 seconds) and then is declared complete, and the printer returns to standby. However there is nothing printed. Is there any new approach to this printer?

---

