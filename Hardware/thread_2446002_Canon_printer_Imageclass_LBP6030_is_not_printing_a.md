---
title: "Canon printer Imageclass LBP6030 is not printing anymore"
date: 2020-06-23
forum: Hardware
---

### Post by pierreu1 on 2020-06-23
This is not a wireless 6030 printer. There was a thread about a wireless 6030, but it did not help me. 

[IMG]https://drive.google.com/file/d/1cV7wiANt8v5UTdC_TdePN3Vh0DFugcB2/view?usp=sharing[/IMG]It used to print everything from anywhere fine, but the last time it printed 1 out of 20 pages and then it stopped. It was a tax document. Maybe that is why! LOL Maybe I was not patient enough.

I tried to print other smaller test documents after, but to no avail.

I checked the usb and power cable. The printer is on. I took out the usb cable to reboot. 

I ran out of ideas on how to make this work. Did I installed the driver too many times? Did I miss a step after?

I noticed I had many jobs "pending" after trying different attempts after trying to download and remove (ad nauseam) drivers and follow advice on the net. I cleaned that up in the utility for the printer.

I included two screenshots to help.

[IMG]https://drive.google.com/file/d/1HrQVcKj25g2Q8oWqPwcg3BFN_sSMZ5PL/view?usp=sharing[/IMG][ATTACH=CONFIG]286284[/ATTACH][ATTACH=CONFIG]286285[/ATTACH]

In HardInfo it states that it is "printing", but nothing comes out.

-Printers (CUPS)-


CUPS-BRF-Printer
LBP6030-6040-6018L        : <i>Default</i>

After some searching , I ran several commands from [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) .

That solved the problem. Not sure what did it. Maybe all that was needed was the

 [COLOR=#333333][FONT=monospace]cancel -a

command to clear the printer.[/FONT][/COLOR]



Much appreciated.

---

