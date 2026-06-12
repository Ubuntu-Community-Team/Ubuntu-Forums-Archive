---
title: "Printer driver for Brother HL-2340DW"
date: 2019-02-25
forum: Hardware
---

### Post by rudolf-kunzli on 2019-02-25
Hello,

I am looking for the printer driver Brother HL-2340DW.
Where can I find this one? I checked the site of Brother without chance. Very confusing.
The questions:
- can you provide me a link for the driver
- is there an installation procedure?

Thanks for advice.
Rudolf

---

### Post by SeijiSensei on 2019-02-25
[https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2340dw_us_eu_as&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2340dw_us_eu_as&os=128)

The "Driver Install Tool" on that page is your best bet, though you'll need to run it from a terminal prompt.

Details here:  [https://askubuntu.com/questions/636363/how-do-i-install-proprietary-drivers-for-my-brother-all-in-one-printer-scanner-f](https://askubuntu.com/questions/636363/how-do-i-install-proprietary-drivers-for-my-brother-all-in-one-printer-scanner-f)

---

### Post by coffeecat on 2019-02-25
The link SeijiSensei posted is really useful, but I noticed an interesting detail. Under compatible models, it lists HL-L2300D in addition to your HL-L2340DW, as well as many other models. A driver for HL-L2300D is already included in Ubuntu 18.04, and I wouldn't be surprised if there is simply one driver for many Brother models, and that the included driver in Ubuntu 18.04 will work with your printer. If so, all you need do is to connect the printer and run the graphical printer utility.

However, you don't specify which release (16.04, 18.04, 18.10) or flavour (Ubuntu, Xubuntu, Kubuntu, Lubuntu, Ubuntu Mate, etc) of Ubuntu you are using. If you post back details someone will be able to tell you how to attempt to install your printer from the GUI without having to download anything, and see if that works.

---

### Post by rudolf-kunzli on 2019-02-25
Thanks a lot for the response.
I am running 18.04 LTS 2
I did connect the printer directly after installing Ubuntu but did not run the graphical printer utility which I don't have...
The printing is a hell of a mess. Printing ALL does print 1 or 2 pages. From page to page does not print in ascending order.
So I need to do something about.

Thanks a lot

---

### Post by brian_p on 2019-02-25
> **rudolf-kunzli said:**
> 
So I need to do something about.


It takes less than 30 seconds to get the HL-L2340DW printing:

[https://wiki.debian.org/QuickPrintQueuesCUPS#IPP_Printers](https://wiki.debian.org/QuickPrintQueuesCUPS#IPP_Printers)

---

### Post by rudolf-kunzli on 2019-02-25
Very nice response...

It takes me 10 seconds to get my HP printers printing on Fedora 29
I am just installing Ubuntu for a friend of mine

Rudolf (founder of Autodesk, Inc and former developer of AutoCAD)

---

### Post by rudolf-kunzli on 2019-02-25
Meanwhile I found this Driver Install Tool - linux-brprinter-installer-2.2.1-1
I guess I'll use this one...
I have to remote login to run it...
Thanks a lot for help

---

