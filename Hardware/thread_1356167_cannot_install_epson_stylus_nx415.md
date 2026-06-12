---
title: "cannot install epson stylus nx415"
date: 2009-12-15
forum: Hardware
---

### Post by sp0tz on 2009-12-15
edit: nevermind, I found out my roommate had an old HP PSC 2355 in the garage. Plugged it in and both printing and scanning worked fine. I got an error about a cartridge alignment failure, but that may be because it's pretty much out of ink. I dunno. Either way, I'm going to go return the POS epson tommorow. Don't buy epson. The damn thing didn't even work on my windows machine.

I just got a good deal on an Epson stylus nx415 printer/scanner/copier, and tried to install it. When I plugged it in, I was given a list of drivers to chose from. The closest thing was the epson stylus 410, which I tried, but it did not work. Firing up Xsane after that gave me a message that said "no devices available". After looking around for a guide for my printer specifically, I found this:

[http://ubuntuforums.org/archive/index.php/t-1266259.html](http://ubuntuforums.org/archive/index.php/t-1266259.html)

Following that guide, I found the proper ppd file for my printer here:

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

I ran into trouble at this step in the guide:

sudo cp /path/to/file/DRIVER_NAME.ppd /usr/share/cups/model

, because that copies the driver file to a file named 'model'. I think the intention was to copy the file into a folder named model, or named after the model of the printer. I'm not sure, this is where things start falling apart. Looking around a bit more, I found that I was supposed to install pipslite. I couldn't find any way to install it; 

sudo apt-get install pipslite

and

sudo pipslite-install

both failed. Now I'm not really sure what to do, but I know my printer doesn't work. I appreciate any help, thanks.

---

