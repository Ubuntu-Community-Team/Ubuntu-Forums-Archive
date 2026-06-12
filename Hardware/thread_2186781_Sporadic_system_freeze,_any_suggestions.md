---
title: "Sporadic system freeze, any suggestions?"
date: 2013-11-09
forum: Hardware
---

### Post by QMMJOO5qnjXFGPEbGog6 on 2013-11-09
This is the current hardware:
Intel Core i3 3225 3.3 GHz
Corsair 8GB (2x4096MB) CL11 1600Mhz VENGEANCE LP
Gigabyte GA-B75M-D3P mATX (F7s bios, HD4000 graphics)
Cooler Master Silent Pro M2 520W 80+ Bronze
1TB WD Blue (tried several different)

Gigabyte GeForce GT 640 2048MB
TBS6280 DVB card

OS have been ubuntu 12.04 and 13.10


The system freezes at random intervals from 20 minutes to 10 days. It shows the screen at the time of the freeze, nothing in the logs and the system is completely unresponsive, no sysreq keys or network contact. A couple of times it displayed black dots on the screen after reboot: [https://dl.dropboxusercontent.com/u/29804668/blackdots.png](https://dl.dropboxusercontent.com/u/29804668/blackdots.png)

Initially the system were without the GT640 and TBS6280 cards, 12.04.
After the initial freezes I ran memtest86+ on all possible combinations of ram sticks, no problem.
For some reason I believed it to be the intel graphics drivers and upgraded to 13.10 in order to get newer drivers but no use (the reason for this thinking was that the system did not crash for three days when booted without a screen).
Then added the GT640 card, I then needed to upgrade the bios from F5 to F7s to get the card running.
Installed a new PSU, one single 12V rail.
Installed ubuntu using both efi and bios.


So now I am thinking of starting to replace parts of this system, what should I replace first? Or are there any other software related things to try?
[FONT=Verdana]

[/FONT]

---

### Post by QMMJOO5qnjXFGPEbGog6 on 2013-11-19
Yeah, well. I changed the motherboard. It is now a

ASRock H61M-DGS mATX

This was the cheapest thing to change, and since I am using it with the old system disks, also a quick change. The only issue was that the PCIEx1 slot speed holding the DVB card had to be set to "1st gen" and not the default "auto".

The system have an uptime of 2 days now. And I am optimistic: Running programs on this machine via X11 is faster (Handbrake and projectx) and also TV recordings (mythtv) now consumes 5% CPU. Earlier it was closer to 70%.

I really have no idea if there is a problem with just my GA-B75M-D3P or if it is a more general problem for this board.

---

### Post by QMMJOO5qnjXFGPEbGog6 on 2013-11-26
And boom! The machine froze after 7 days.

Again memtest86+ shows no problem with the RAM. And since the machine also froze using single RAM sticks: either both RAM sticks are faulty (and does not show it in memtest86+)  or the CPU is to blame.

The current motherboard is using 1.6V as RAM voltage by default, the RAM is OK from 1.2V and up to 1.6V. I am now fixing the RAM voltage at 1.5V and CAS 11-11-11-30 (XMP)

From [http://www.overclockers.co.uk]("http://www.overclockers.co.uk/"):
> 
[COLOR=#333333][FONT=verdana]Vengeance LP Performance Memory modules, 8GB (2x4GB) DDR3 1600MHz CL22 Unbuffered DIMM Memory for AMD, Intel Processor platforms, including 2nd and 3rd generation Intel Core i7 and i5 systems. Every Vengeance memory module provides users with outstanding performance and high quality. Vengeance memory modules are built using carefully selected DRAM to allow excellent overclocking performance and rock solid stability.[/FONT][/COLOR]

[COLOR=#333333][FONT=verdana]Features[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- 8GB Modules[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- Each twin module set is tested at 1600MHz[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- Vengeance LP heat spreader for styling and performance[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- Packaged together immediately following system test[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- Tested together at 1600MHz, Vdimm = 1.50V, at latency settings of 10-10-10-27 on Intel DDR3-based motherboards.[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- SPD programmed at: JEDEC standard 9-9-9-24 values at 1333MHz.[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- XMP 11-11-11-30 values at 1600MHz, 1.50V[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- 8192 Megabytes of DDR3 memory[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- Two matched 4GB modules[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- 100% tested at 1600MHz in Intel based motherboards[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- Supports Intel Extreme Memory Profiles (XMP)[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- Lifetime Warranty[/FONT][/COLOR]
[COLOR=#333333][FONT=verdana]- Sandybridge/Ivybridge compatible[/FONT][/COLOR]

---

### Post by QMMJOO5qnjXFGPEbGog6 on 2013-12-31
Nope, crashed again.

So I changed the RAM, now:

A-Data 8GB (2x4GB) CL9 1600MHz XPG INET EDITION


And now the machine runs as expected, stable for the last 25 days.

So the old RAM passed memtest86+, both as single RAM sticks and as a pair. In two different motherboards. But crashed sporadically as single RAM sticks and as a pair.

---

