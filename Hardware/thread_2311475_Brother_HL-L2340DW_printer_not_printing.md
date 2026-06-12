---
title: "Brother HL-L2340DW printer not printing"
date: 2016-01-27
forum: Hardware
---

### Post by PDA1 on 2016-01-27
I'm running Ubuntu 12.04 and just bought a Brother HL-L2340DW laser printer (wireless connection).

My system "sees" the printer and it appears as the default (only) printer.

The problem is when sending a job to be printed no printing occurs.  The error message that appears on the screen is; "Printing Cancelled"...

No, I didn't cancel the print job.

Can someone tell me how to get my machine to print wirelessly to that Brother printer?

By the way, after contacting (big) "Brother" and they wasting my time in getting my name, rank and serial number the talking head said to download the drivers from our website.  

I followed their instructions but still no solution.

---

### Post by Kato4059 on 2016-01-27
Suggest you download ,from Synaptic the Brother packages that pertain to your model ,or as close as can be ,also install csh and Tcsh files they could help. I have always had trouble with the Brother printers in linux.
Best of luck.

---

### Post by PDA1 on 2016-01-27
What are csh and Tcsh?

---

### Post by PDA1 on 2016-01-27
Solved!

Man, was that easy!

1- Print a "Printer Settings" page using the keypad on the HL-L2340DW.
2- Locate the printer's IP address part way down the Printer Settings sheet.
3- While in Ubuntu 12.04-------->System Settings------>Printers

Add Printer------->Find Network Printer-------> enter the IP address in the "Host" place.  The program will locate your printer in a few seconds.

Geez, if I can do it....anyone can.

---

