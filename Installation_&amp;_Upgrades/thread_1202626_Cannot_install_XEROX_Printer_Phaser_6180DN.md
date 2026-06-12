---
title: "Cannot install XEROX Printer Phaser 6180DN"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by andrewma on 2009-07-02
Hello,

I am trying to install XEROX printer phaser 6180DN.  I think the CUPS installation return an "Internal Error" at the last step.  According to the log, it seems to have something to do with "LSB"...

Thanks
--Andrew

---

### Post by halitech on 2009-07-03
did you download the PPD files from Xerox?

[http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=6180&Xlang=en_US&Xcntry=USA](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=6180&Xlang=en_US&Xcntry=USA)

Download the Linux CUPS Printing Package, extract them and then install the printer using CUPS. When it asks for the Make/model, browse to where you extracted the files and select the correct model.

---

