---
title: "Canon Pixima IP1600 CUPS Error"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by Guardian-Mage on 2007-10-19
[http://www.northernlightstech.com/printerror.png](http://www.northernlightstech.com/printerror.png)

I have Ubuntu 7.10. Which should automatically configure my printer but it didn't. It added it and set it as the Default Printer but whenever I print in OpenOffice it just said error, So I went into Menu > System > Administration > Printing and tried to do a 'Print Test Page' and it came up with the error in the above screenshot. I really need my printer so how can I fix it.

---

### Post by Guardian-Mage on 2007-10-20
Non I print a test page and nothing happens.
followed [http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html](http://arzanulhaq.blogspot.com/2007/06/how-to-setup-canon-pixma-ip1600-and.html)

---

### Post by Sef on 2007-10-20
Read [Openprinting.org]("http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1600") (Canon IP1600).

---

### Post by Guardian-Mage on 2007-10-21
I followed the exact guide I found at ([https://answers.launchpad.net/ubuntu/+question/5166](https://answers.launchpad.net/ubuntu/+question/5166)) and now I print and nothing happens. It doesn't even show up in the printer que, was is going on?

---

### Post by Lil on 2007-10-21
I've had no problems with my iP1500 after installing the drivers from here:

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/)

What I would recommend you do is:

[LIST=1]
[*]Remove whatever you have installed (Synaptic Package Manager should help you here in Administration > Printing and searching for the package you installed if you don't know what it is) in case it conflicts with the instructions below here.
[*]Go to Administration > Printing and delete any installed printers making sure the iP1600 isn't plugged in
[*]Go to the above page and read the instructions carefully and then install the drivers for the iP2200 listed on that page. Read the page carefully, you need to add that chap's repository to your sources.list -- ignore the fact that he says they are for Edgy Eft, I found they work great on Edgy, Feisty and Gutsy
[*]Plug in the iP1600 and Gutsy should detect it straight off, it did for my iP1500 once I got the driver installed. If it doesn't click the balloon it pops up to select a driver and choose iP2200 from the Canon subsection. Hopefully whatever you have installed won't foul up.
[/LIST]

Really hope this helps, Gutsy is much better with printing once you have the driver installed, plug in and go once it has that.

I was able to install the iP1500 driver, plug in and just go. Mind you Feisty wasn't that hard either but once the driver is there, this is now easier than Windows and Mac OS X.

Vicky

---

### Post by Guardian-Mage on 2007-10-22
I Just did that and it detected my printer fine, said it was going to use ip1000 driver. That didn't work so I tried the 2200 and 1500 drivers, nothing happens.

---

### Post by rsambuca on 2007-10-23
Have you tried this page?  

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP2200)

---

### Post by Guardian-Mage on 2007-10-24
Thank You, It Worked, Thanks So Much!!!!!!!!!!!!:ks

---

