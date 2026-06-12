---
title: "HP Printers - turn off color?"
date: 2011-11-22
forum: Hardware
---

### Post by lile001 on 2011-11-22
I have two HP printers - a 7500A and a 6110.  I am a cheapskate and want to print everything in black-and-white, by default.  I have a special printer set up just for that purpose (a copy of the regular printer), which is also the default printer.  In system-config-printer, there are some options to turn off color printing, such as under Printer Properties: Printer Options:Output Mode, which i have set to Black Only Greyscale. 

Nonetheless, if I print something in color, it prints in color.  Within the application print menu, I can drill down and find a color print option and turn it off, tediously, every time I print, which wears thin after a while.  Color cartridges are like $40 freaking dollars.  IS there some way to make a printer ALWAYS print in greyscale?

---

### Post by Paddy Landau on 2011-11-29
I think I had the same problem once. I think -- but I'm not sure -- that I solved it like this:


[LIST]
[*]Install [hplip-gui]("apt:hplip-gui")
[*]Open HPLIP Toolbox
[*]Print Settings > General > Output Mode > Black Only Greyscale
[*]You may need to log out and in again.
[/LIST]

Let me know whether or not this works for you.

---

