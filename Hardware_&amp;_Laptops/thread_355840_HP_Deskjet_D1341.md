---
title: "HP Deskjet D1341"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by passonno on 2007-02-07
Hello,

Just got a Deskjet D1341, worked fine in WinXP, though I have since entirely ditched windows.

It is apparently seen in Dapper, though it does not seem to want to print anything.  

Anyone have any clues?

thanks

---

### Post by H.E. Pennypacker on 2007-02-27
Have you tried this:

[http://wiki.kevindriscoll.info/wiki/Setting_up_HP_Deskjet_D1341_with_Ubuntu_Linux](http://wiki.kevindriscoll.info/wiki/Setting_up_HP_Deskjet_D1341_with_Ubuntu_Linux)

For future reference, you may not want to buy a printer that is not listed on LinuxPrinting.org.  That'd be too risky.

---

### Post by Smuve on 2007-03-31
Hi passonno.  If you're still monitoring this thread, I just installed a D1341 and it is working beautifully.  I had a Canon and bought the D1341 specifically for Linux compatibility.  Since they are being bundled for free with new computers, these things are going for cheap on ebay.

The D1341 is not listed in Linux Printing, but I think the 1360 is (it's been a few days since I looked it up).  They're both 1300 series printers and use the same drivers listed on HP's site.

I don't know what version of hplip you have installed but the latest works great.

Download hplip-1.7.3.run from: 
[http://hplip.sourceforge.net/]("http://hplip.sourceforge.net/")

Follow the instructions here:
[http://hplip.sourceforge.net/install/install/index.html]("http://hplip.sourceforge.net/install/install/index.html")

This will install all dependencies and remove your old version, if you have one installed.  "It's automatic, baby."

Note:  Choose "no configuration" in the Postfix section.  *I didn't read the directions.

My printer is installed on a print server, so for some reason, HP's configuration tool couldn't find.  So I just went to Add New Printer and it was like butta'.

Tip:  When selecting the driver, the D1300 is listed after all the other numbered printers.  It's not in the 1000 range where I was looking, letters come after numbers in alphabetical order.  Maybe it was in my installed version, but I couldn't find it the first time, thus I installed 1.7.3.

---

