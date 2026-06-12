---
title: "CUPS printing on Zebra printer"
date: 2015-12-02
forum: Hardware
---

### Post by young6 on 2015-12-02
Hi,


I have the following setup.


**Ubuntu server **with CUPS installed***----***------ (TCP) --------> **Windows print server **with Zebra driver installed*-------------*-- (TCP) ------------> **Zebra printer **GK420d



In CUPS, I configured the Zebra printer using TCP with the printer's IP address at port 9100, along with the ZPL driver.

That is, it's not going through the Windows print server because when I tried using LPD, even a text file could not be printed (the printer's LED blinks but nothing gets printed), so I configured CUPS to use the direct TCP printing instead.



I have no problem printing a plain text file directly to the printer (via TCP socket printing in CUPS) from Ubuntu shell.

But, if I send a PDF file, it gets stuck forever in the print queue and I have to manually cancel it.


If I check the CUPS mime.convs file, I see a conversion definition to use **pdftops** and I do have the **pdftops **executable file in the filters directory.


What could be wrong with my PDF printing and how can I fix it?


Thanks much in advance!



- Young

---

### Post by efflandt on 2015-12-06
There are some cups instructions on [https://www.zebra.com/us/en/support-downloads/desktop/gk420d.html](https://www.zebra.com/us/en/support-downloads/desktop/gk420d.html) fairly generic, but they do mention Ubuntu and have a link in that file to Zebra's knowledge base. It does not mention how to tell anything the label size.

Are your PDF files the size of the label and are they landscape or portrait? Does the test page work from Ubuntu? I don't know if cups has a way to automatically size a page to fit the paper because when I scanned something else as US letter size 300 dpi png to clean it up and then saved it from gimp (which apparently assumed 72 dpi) as pdf, it only printed the center part of the pdf huge on letter size paper (postscript laser printer). Although, when I told gimp it was 300 dpi and saved it as pdf again, then it printed correct size.

I know that at work it was difficult to initially configure Word to print landscape on 2" wide x 4" labels on a network Zebra 2824 or display properly in Word without being rotated 90 degrees counterclockwise to portrait with sideways print. Eventually I figured out how to have it both display in Word as landscape and print that way.

It was more problematic trying to access Windows shared USB Zebra 450 (UPS) and 505 (FedEx) printers from our shipping computer. The shipping computer can print from Word directly to the 450 used for UPS, but even though the shared printers were visible on the network, I could not figure out how to network print to them at all from Windows (not even test page). But that may have been because UPS also had its own driver for the 450 and one of the printers showed both ZPL and EPL printers.

---

### Post by oldfred on 2015-12-06
Years ago we used Zebra label printers with ZPL to print labels. But we used Basic in Windows and had to use a Windows generic ASCII driver that sent no print codes to printer. Every code had to be the ZPL.

In Korea I had huge issues as the Korean Windows did not have the standard Windows ASCII printer driver as ASCII did not support the extra characters. One of our programmers in USA sent me a driver so I could install it.

I do not think a pdf file will have the internal codes to format using ZPL, even with a new Zebra printer driver that may let you use other formats??

---

### Post by SeijiSensei on 2015-12-06
If you configure the Windows print server to share the printer, you can print to it from CUPS using an "smb://" URL.  That would use the Zebra driver on the Windows machine.

---

### Post by lite.m.finocchiaro on 2016-06-15
I know this is an old thread, but I figured I would chime in, as I've been using a Zebra label printer with CUPS and Ubuntu for years now.

For raw printing (EPL, ZPL), you have to use a generic text-only raw queue.

For PDF/Image/Pixel-based printing, you have to use the zebra driver. Make sure you specify the size of your label stock in CUPS and the orientation, as there can be several setups, and the default one isn't always right for your printer.

In Windows, the driver understands both raw and pixel-based jobs and sends the jobs as such. In CUPS, however, you need both queues, even though they point to the same printer.

Feel free to shoot me an email at [email]lite@qz.io[/email] if you have any questions.

---

