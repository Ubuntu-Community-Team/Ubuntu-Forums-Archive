---
title: "Printer is haunted!"
date: 2008-08-25
forum: General Help
---

### Post by mahela007 on 2008-08-25
Yeah.. I have a canon BJC 265sp and I installed it on ubuntu. I found the exact driver and the install went well enough. However now every time I turn my computer on while the printer is connected to the computer it starts printing and it wont stop. Whats more it prints what looks to me like utter gibberish. (stupid characters and such like) And every time the printer is turned on this happens. The only solution I have found is to turn the printer off.
Whats happening? I know nothing is wrong with the printer because I used it with my windows PC and nothing happened.

---

### Post by prshah on 2008-08-25
> **mahela007 said:**
> However now every time I turn my computer on while the printer is connected to the computer it starts printing and it wont stop. 

It may be printing a "stale" job; one that you have started last time and then interrupted. Open the [CUPS administration page]("http://127.0.0.1:631") and delete all pending jobs.

Then turn on your printer again. It should not print junk anymore.

If every print is giving you junk. it is very likely you have installed the wrong postscript/pcl driver. If you have the option to use PS (postscript) or PCL (Printer Control Language), try toggling the options.

---

### Post by Crafty Kisses on 2008-08-25
You may want to look over these

[http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters)
[http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors](http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors)

---

