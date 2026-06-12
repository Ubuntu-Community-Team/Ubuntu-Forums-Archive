---
title: "LPR printing problems with Brother DCP-7030"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by mychance on 2009-10-15
Hi,

I have a network print server device (a no brand name) and printing is INCREDIBLY SLOW, next to frozen actually.  I see that the printer (Brother DCP-7030) is receiving the data and I see the printing status window showing that the printing is in progress but it always stays at 0%.  When someting comes out from the printer, it is a partial image with long vertical lines followed by a whole bunch of blank sheets.

Both the print server and the printer work flawlessly with the computer booted in Win XP, so the print server is allegedly in good working order.  I have installed both the CUPS wrapper and the LPR drivers from the manufacturer website.  The printer prints flawlessly when connected on USB so the driver is allegedly good.

The problem occurs in the same fashion on my two Linux systems (Ubuntu and Linux Mint).

I have made the LPD installation in the following manner: New printer -> LPD/LPR Host or Printer.  I input the IP address of the print server and choose the same driver in the list than the one that works with USB.

I am not an expert on Linux but I know how to type a command or change a line in a config file :)

A thousand thanks if you can help me solve this problem !

---

### Post by kocur on 2011-01-23
I have actually very similar problem with the same printer - [http://ubuntuforums.org/showthread.php?t=1673624#post10387522]("http://ubuntuforums.org/showthread.php?t=1673624#post10387522") ...have you found the solution???

Thanks!

---

### Post by Raubsau on 2011-01-29
For Ubuntu 10.10 Maverick:

Unplug printer

Goto: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7030](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7030)
Download: [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brdcp7030lpr-2.0.2-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brdcp7030lpr-2.0.2-1.i386.deb&lang=English_lpr) (LPR)
Download: [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperDCP7030-2.0.2-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperDCP7030-2.0.2-1.i386.deb&lang=English_gpl) (cupswrapper)

in terminal:
```
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model
sudo dpkg -i --force-all brdcp7030lpr-2.0.2-1.i386.deb
sudo dpkg -i --force-all cupswrapperDCP7030-2.0.2-1.i386.deb
```
Shutdown, plug in printer
Add Printer in GNOME dialogue, it will show up as "Brother DCP 7030 for CUPS" or similar.

---

