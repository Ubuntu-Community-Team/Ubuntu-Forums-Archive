---
title: "&quot;Printing bridge&quot; on Ubuntu"
date: 2013-09-27
forum: Hardware
---

### Post by GrayJack on 2013-09-27
Hi All!

Not sure this is a right topic here but I cannot find anything closer to it.

We have a small office network with the following PCs:
1. WinXP with connected printer Canon LBP-1120.
2. Several Windows 7 (including x32 and x64). There is no Win7 driver for Canon LBP-1120, so they cannot use these printer in network
3. Ubuntu 12.04.03 LTS that works ok with Canon.

Is it possible in any way to establish some kind of "printing bridge" on Ubuntu PC so it will be possible to use Canon printer on Win7 PCs? I mean to use some kind of network printer on Ubuntu to overcome the absence of Canon LBP-1120 drivers for Win7?

Thank you in advance for possible help.

---

### Post by scbingham on 2013-09-27
You want to set up a "print server" on the Ubuntu pc.

Read this:
[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

Good luck

---

### Post by GrayJack on 2013-09-27
Thanks for your reply.
Sure I've read that info because it was me who installed above mentioned printer in Ubuntu system. Without that topic I am not sure I could do it.
As for my question - that info doesn't help much. The closest case is [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) but it is nothing because:
> 2) Windows will ask you to select a driver for the  printer. If you have the Windows print drivers, you should use them.  Click the "Have Disk" button and select the .inf file that describes  your print drivers. 

If  you do not have the drivers for the printer or cannot load the .inf  file, you should select the "MS Publisher Color Printer" driver from the  "Generic" manufacturer. This driver should be found on all Windows 2000  and XP installations by default and it gives all the printing  functionality one should need.

As I said there is no driver for Win 7. And "generic' printer works ugly.

What I expected as a help: possibility to send to Ubuntu some kind of image of printing document - possibly pdf or ps - and automatic printing of this image on Canon printer.

---

### Post by scbingham on 2013-09-27
How about the win7 pcs printing to pdfs onto a ntfs partition on the Ubuntu pc. Then having a script/cron job running which checks & prints any new pdfs to the Canon printer?

---

### Post by GrayJack on 2013-09-30
This is closer! Thanks for an idea!

Is it possible to use cups-pdf as a Network Printer on Win 7 guests to avoid installing some pdf virtual printers / converters?
If so - where can I find drivers for /var/lib/samba/printers for that?

---

