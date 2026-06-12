---
title: "Brother MCF-J835DW &amp; Raring"
date: 2013-04-23
forum: Hardware
---

### Post by jetsaredim on 2013-04-23
I've had this printer for a couple of months and it worked pretty well under 12.10.  I just recently upgraded to 13.04 over the weekend and I'm trying to get everything working again and I can't seem to get the printer to work.  Brother has what would seem like really good support for Linux, but for some reason their install procedures don't seem to work completely under my new install.

I'm working off the instructions found here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

I have the printer setup on my network wirelessly connected.  I know the printer works as I'm able to use the Brother app from my Android phone and tablet.

There is some amount of auto-detect going on with the printer as it automatically sets up a CUPS printer entry during the install of the brother debs.  I can see and manage the printer through the CUPS administration as well as through the printer dialogs in the System Settings menus.  I've verified the settings in the CUPS administration are correct (correct ip address).  So, I'm not quite sure what the issue might be.

The only thing I can think of is that my user account (which is pretty much the default setup) might possibly not be setup to print or something ridiculous like that, but other than that I can't think of anything.

Any help or advice would be greatly appreciated.

TIA

---

### Post by pdc on 2013-04-23
If you copy and paste

> [COLOR="#FF0000"]sudo dpkg -l | grep Brother[/COLOR]

this will list what Brother drivers you have installed......you could post the results back here .......the above command contains a pipe command symbol.......

if you paste this [http://localhost:631/printers/](http://localhost:631/printers/) into a spare browser window it will show what is set up in CUPS

---

### Post by jetsaredim on 2013-04-23
$ dpkg -l mfc*
ii  mfcj835dwcupswrapper                                                    3.0.0-1                                  i386                                     Brother CUPS Inkjet Printer Definitions
ii  mfcj835dwlpr                                                            3.0.0-1                                  i386                                     Brother lpr Inkjet Printer Definitions

(same results as your suggested command)

As I mentioned, I had checked the settings from the CUPS admin page and they seemed correct, so the CUPS printer listing should show the same information.

---

