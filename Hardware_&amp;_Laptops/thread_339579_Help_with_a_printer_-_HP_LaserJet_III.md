---
title: "Help with a printer - HP LaserJet III"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by Aterian on 2007-01-16
I'm having trouble getting an HP LaserJet III that I've had around for a while working on my Ubuntu system (an Athalon 2000 running Edgy).  The printer works fine.  Up until about a weak ago I had it attached to a D-Link [DI-704P](http://www.dlink.com/products/?pid=63&sec=0) (which can act as a print server for LPT printers) on my home network.  It just died a week ago, and all the windows computers on my network could use it fine with their default HP LJ III drivers as recently as about a week and a half ago.

I wanted to move the printer to the Ubuntu system and use Samba's printer sharing (the system already does some file sharing with samba) to get the printer back on the network.

However, I'm having problems getting the system to communicate with the printer.  When I try to add it as a new printer (in gnome), here's what I'm doing:

[list]
[*]System->Administration->Printing
[*]New Printer
[*]*Note: No printers are auto detected*
[*]Use another device: LPT #1
[*]Manufacturer: HP
[*]Model: LaserJet 3
[*]Driver: ljet3 (recommended) (Suggested)*
[*](Default values for the name/description page)
[/list]


[size=-2]* For the driver, I also tried going to linuxprinting.org and downloading and installing the driver for this printer manually.  This has the same results.[/size]

After this, the new printer shows up in the Printing menu with status "Ready"

At this point, I went to the printer's properties screen and tried to print a test page.  Looking at the printer, the Form Feed light turns on, then the Ready light blinks on and off for about 10 seconds (usually this means it's communicating, so far so good), but after about 10 seconds, the On Line light turns off and the LCD displays "MEM OVERFLOW"  Resetting the printer with the reset button causes the job to complete in Ubuntu and the printer to print a garbage page.

As a side note, I had the cupsys and hplip services turned off before I tried to install it, but enabled them again and they appear to be running.  At least, I see the following after running ps -lA:

> 
F S   UID   PID  PPID  C PRI  NI ADDR SZ   WCHAN  TTY          TIME CMD
...
5 S     0 19026     1  0  75   0          -   5323 362145  ?        00:00:00 hpiod
...
5 S   105 23646     1  0  76   0         -  1183      -      ?        00:00:31 cupsd
...

Any help is greatly appreciated - Thanks in advance..

---

