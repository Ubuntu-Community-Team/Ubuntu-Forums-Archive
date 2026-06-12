---
title: "How do I install a printer driver?"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by wersdaluv on 2007-08-16
I am trying to make an HP 900 Inkjet Printer to work on Ubuntu Feisty.

I found this thread--> [http://ubuntuforums.org/showthread.php?t=503507&highlight=hp+inkjet+900](http://ubuntuforums.org/showthread.php?t=503507&highlight=hp+inkjet+900)

A  guy from the thread recommended this driver--> [http://openprinting.org/show_printer.cgi?recnum=HP-910](http://openprinting.org/show_printer.cgi?recnum=HP-910) but I do not know what to do with the page he gave me. What do I do with the files from the page?

:guitar:

---

### Post by linuxwizard on 2007-08-16
HP printers are easy to setup. Just follow this don't do anything else. Post back 



Local Printing

A local printer is one which is directly connected to your computer (as opposed to a network printer, discussed in the following section). To setup a new local printer:

   1.

      Obtain the model name of your printer.
   2.

      Ensure the printer is turned on.
   3.

      Choose System &#8594; Administration &#8594; Printing
   4.

      Now choose Printer &#8594; Add Printer.
   5.

      Your printer should be automatically detected. If so, simply click Forward and then Apply.
   6.

      Finally, you can enter in a description and location for your printer.

If your printer was not automatically detected, you can try to select the port and printer driver manually. Some printers need further setup. Search the databases at LinuxPrinting.org or check the Ubuntu Wiki's Printer page for possible information on your printer.


[https://help.ubuntu.com/7.04/printing/C/printing.html#local](https://help.ubuntu.com/7.04/printing/C/printing.html#local)

---

### Post by wersdaluv on 2007-08-16
> **linuxwizard said:**
> HP printers are easy to setup. Just follow this don't do anything else. Post back 



Local Printing

A local printer is one which is directly connected to your computer (as opposed to a network printer, discussed in the following section). To setup a new local printer:

   1.

      Obtain the model name of your printer.
   2.

      Ensure the printer is turned on.
   3.

      Choose System &#8594; Administration &#8594; Printing
   4.

      Now choose Printer &#8594; Add Printer.
   5.

      Your printer should be automatically detected. If so, simply click Forward and then Apply.
   6.

      Finally, you can enter in a description and location for your printer.

If your printer was not automatically detected, you can try to select the port and printer driver manually. Some printers need further setup. Search the databases at LinuxPrinting.org or check the Ubuntu Wiki's Printer page for possible information on your printer.


[https://help.ubuntu.com/7.04/printing/C/printing.html#local](https://help.ubuntu.com/7.04/printing/C/printing.html#local)


Thanks for the reply! 

:KS

I was trying to install a local printer.

After the printer was detected, when I was to choose the appropriate driver, the model of the printer was not there. It has been discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=503507&highlight=hp+inkjet+900") that it really is the case. Someone from that thread suggested his HP Inkjet 910's driver which can be found [here]("http://openprinting.org/show_printer.cgi?recnum=HP-910") but I do not understand what the page suggests.

Are there any workarounds?

:KS

---

### Post by FuturePilot on 2007-08-16
I think what you need to do is download the .ppd file from that page. Here's a direct link ;)
[http://openprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-910&show=0]("http://openprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-910&show=0")
Then start the install process and when it comes to the point where you pick the driver, click Install Driver. Then just navigate to the .ppd file. I think that should do it.

---

### Post by linuxwizard on 2007-08-16
After printer is detected take the recommended driver or default should be hpijs if 900 is not there is the 910 use that.

---

### Post by wersdaluv on 2007-08-16
Do I install it like any other bin file?

EDIT:
Oh... I got it.. I point to that driver. :D

---

### Post by wersdaluv on 2007-08-16
Thanks! :)

---

### Post by linuxwizard on 2007-08-16
So what did you do ? Did you install driver or picked it from the list  using 910 ?

---

### Post by wersdaluv on 2007-08-17
It works now! 

I got the driver from the link and chose it as the driver for the detected printer. 

:KS

---

