---
title: "Problems with lexmark x75 need a howto"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by KHCloud on 2007-01-17
Need help installing a lexmark x75 printer on edgy(6.10). The official page for the printer is here: [http://www.lexmark.com/lexmark/product/home/519/0,6970,204816596_653399443_248488455_en,00.html?tabId=1](http://www.lexmark.com/lexmark/product/home/519/0,6970,204816596_653399443_248488455_en,00.html?tabId=1)

Any help would be appreciated, thanks!

---

### Post by smd0665 on 2007-03-28
Yes, I have the same problem. The printer responds when I use the Z31 driver, but it doesn't actually print - it only feeds the paper. Does anyone have a solution? Thank you.
I'm also using Edgy.

---

### Post by ramjet_1953 on 2007-03-30
The only info that I can find is here:
 [http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X75](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X75)

I hope that it helps.
Lexmark are renowned for their lack of support outide Windows.

Regards,
Roger 8)

---

### Post by MikeSho on 2007-10-21
Please follow the instruction below to install lexmark x73 - 75 on Ubuntu 7.10. Mine worked perfectly fine so your should as well.

Open a terminal and enter the following Codes:

1.   sudo apt-get install libcupsimage2-dev libcupsys2-dev libtiff4-dev libtiffxx0c2

2.   cd /home/elizabeth/lxx74-cups-0.8.4.2

3.   make

4.   sudo make install

Expected Output:

lxx74.install 
Installation done.


Finished. You are done. Just add the printer through System, Administration, Printing and choose the new driver and NOT the recommended one that came with 7.10.

I'll post that for the scanner once I'm done.

---

### Post by MikeSho on 2007-10-21
Don't forget to change elizabeth to your own name as applicable

---

### Post by smd0665 on 2007-11-16
> **MikeSho said:**
> Don't forget to change elizabeth to your own name as applicable

Well, I'm fine until I get to the "adding printer" part. I'm using KDE. I go to System Setting/Printers, then Add Printer/Class. I choose "Local Printer", then URI:usb://Lexmark/All%20In%20One. I choose Manufacturer:Lexmark and click on "Other." Then, I change to the lxx74-cups-0.8.4.2 directory. I've tried the lxx74.drv, but I get the following error: 

Wrong driver format. /home/smdias/lxx74-cups-0.8.4.2/lxx74.drv(line 50): syntax error, unexpected KEYWORD, expecting '/' or ':'

 In fact, I've tried everything in this folder and they all give me error messages. Any ideas?

---

### Post by smd0665 on 2007-11-18
Okay, I installed the Gnome desktop on top of Kubuntu and I can select the driver that way. I think now that there is a problem with my printer, though. It responds, but then I get a blinking status light. It does the same thing when I hook it up to a Windows machine now too. The scanner works fine, though (which is really what I'm interested in). Thanks for the help, MikeSho. This has been plaguing some of us for a while.

---

### Post by in_flu_ence on 2007-11-27
I actually manage to install properly and added my printer as All in One. Manage to print
However, the left and right adjustments are not right. Seems that the page is shfited to the left. How can I adjust the alignment?

thanks

---

### Post by folfos on 2008-06-05
i did all of that and i got this

felipe@Felipe-Olfos:~/lxx74-cups-0.8.4.2$ sudo make install
bash lxx74.install
lxx74.install: Error: Unable to locate the CUPS model directory (where the PPD files are stored).
Aborting.
make: *** [install] Error 1

can anyone tell me what im doing wrong
also i have ubuntu 8.04

---

### Post by cothedo on 2008-06-30
> **MikeSho said:**
> Please follow the instruction below to install lexmark x73 - 75 on Ubuntu 7.10. Mine worked perfectly fine so your should as well.

Open a terminal and enter the following Codes:

1.   sudo apt-get install libcupsimage2-dev libcupsys2-dev libtiff4-dev libtiffxx0c2

2.   cd /home/elizabeth/lxx74-cups-0.8.4.2

3.   make

4.   sudo make install

Expected Output:

lxx74.install 
Installation done.


Finished. You are done. Just add the printer through System, Administration, Printing and choose the new driver and NOT the recommended one that came with 7.10.

I'll post that for the scanner once I'm done.

I was able to reproduce step one, but I run into trouble with step two. I could not get it to work. I changed "cd /home/elizabeth/lxx74-cups-0.8.4.2" to "cd /home/emiel/lxx74-cups-0.8.4.2", but that failed with the message that the file or folder didn't exist. I then typed "whereis lxx74-cups-0.8.4.2", but that does not return any result.
I'm new to Ubuntu so I'm afraid you're going to have to spell it out for me...

---

