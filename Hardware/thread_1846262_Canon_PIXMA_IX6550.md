---
title: "Canon PIXMA IX6550"
date: 2011-09-18
forum: Hardware
---

### Post by josvanr on 2011-09-18
I'm thinking of buying this printer but have a difficult time finding out if it works on linux... Anybody?

josvanr

---

### Post by danboid on 2012-01-05
It may be a bit late of a response to be of any use to the OP here but I bought my girlfriend this printer for use with Linux and we're very happy with it.

It doesn't seem that CUPS comes with the correct driver for this model so we had to install the Linux drivers available on Canons website. There was an 'install.sh' install script included with the drivers that installs the correct driver but for us it failed when trying to detect the printer to add it as an available output device but this was no big deal because if you go to:

localhost:631

AKA The CUPS web gui and add your printer that way it will find the correct driver installed from the Canon package. Canon include a graphical tool with the Linux drivers that can be used to set print/paper type and quality as well as perform routine maintenance tasks and I would note that although this tool doesn't report ink levels there's no need as you simply need to look at the red LEDs next to each ink cartridge as these blink slowly when ink is low and quickly when its empty.

Good Linux printer indeed! Congrats Canon!

---

### Post by crazy bird on 2012-01-05
> **josvanr said:**
> I'm thinking of buying this printer but have a difficult time finding out if it works on linux... Anybody?
 
josvanr
 
Canon is known for it's poor support to Linux. But there are some solutions. Check for a solution: [https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers](https://sites.google.com/site/tipsandtricksforubuntu/printer-info/canon-drivers).

---

