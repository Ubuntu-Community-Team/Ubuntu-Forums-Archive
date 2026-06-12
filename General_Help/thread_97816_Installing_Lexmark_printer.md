---
title: "Installing Lexmark printer"
date: 2005-12-01
forum: General Help
---

### Post by ellisd_p on 2005-12-01
Could someone be so very kind and help me installation of  a Lexmark Valuewriter 300 to my Ubuntu system.  Ihave been worlking all afternoon with no progress.  

Thank in advance to those whom are about to help me.

Dennis Ellis

---

### Post by Mustard on 2005-12-01
I believe Lexmarks can be difficult to impossible to get working.  Try these links to see if you can find your model among them.

[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)
[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

Additionally you can try searching via the forum search function or google for people who have documented their experiences with that model.

---

### Post by Evil Whisper on 2005-12-02
Hello ellisd_p,

I think i found a driver for your Lexmark Value Writer 300 :-)

[http://www.linuxprinting.org/show_driver.cgi?driver=ljet2p&fromprinter=Lexmark-Valuewriter_300](http://www.linuxprinting.org/show_driver.cgi?driver=ljet2p&fromprinter=Lexmark-Valuewriter_300)

**Installation Instructions:**

Goto the above link and choose Lexmark Value Writer 300.
Make sure the download option is selected then click "Generate PPD File".
Next save it to some place such as your home directory or wich ever directory you would like.  Click on System > Administration > Printing.  Then click on "New Printer" and then select "Local Printer" and click forward.  Next choose Lexmark as your manufacturer and then click "Install Driver" then click on the PPD file you saved and then click apply.

Hope this helps,
Evil Whisper

---

