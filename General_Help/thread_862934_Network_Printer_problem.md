---
title: "Network Printer problem"
date: 2008-07-18
forum: General Help
---

### Post by dgonza9 on 2008-07-18
I'm pretty new.

Quick question. I have a printer that is considered a linux "Paperweight" by linuxprinting.org. I'm wondering if I can install the printer on my windows box, then print from my linux box to it as a shared network printer.

I've tried a few things and it's not working out, so I figured I'd better check to see if it's possible.

Thanks.

---

### Post by ramjet_1953 on 2008-07-18
This link may be of use to you:

[https://help.ubuntu.com/8.04/printing/C/printing.html#network](https://help.ubuntu.com/8.04/printing/C/printing.html#network)

Regards,
Roger :cool:

---

### Post by dgonza9 on 2008-07-18
I've tried all that with no success, unfortunately.  

Does it matter that the printer is not supported at all in linux? 

I am able to use pyneighborhood to access files on the windows computer from my linux box, but it does not find the printer on the windows box that is set for sharing when I go to add a printer.

Guidance is much appreciated!

---

### Post by ramjet_1953 on 2008-07-19
No, it shouldn't matter that it is not supported in Linux, as you are using the Windows box as a print server.

I assume, of course, that this printer has been successfully installed on the Windows box and is working fine on that machine?

Also, can you access the Windows machine from your Linux machine? i.e. Can you see the hard drive and access files on the Windows machine?

Regards,
Roger :cool:

---

### Post by dgonza9 on 2008-07-19
The printer works great on windows.  I can access windows machine files with pyneighborhood just fine.

I guess I'm not sure how to properly add the printer or set up samba, though I've followed the guide.

When I add the printer as "windows printer through samba" or "SMB" printer, I don't really know what to put for the address.  I just put the windows box IP address and the name of the shared printer on the windows box.

What I don't understand is why the add printer process then has me pick a model printer AND A DRIVER.  Then when I try to print to the windows box I have the same performance as when I had it hooked up to the printer.

As I've said, the print jobs go to the XP box, but it appears to be using the linux driver and therefore not working.

Thanks for the help.  I spent like 10 hours trying to fix this the past few days and my wife is mucho pissed off.

---

### Post by lswb on 2008-07-19
One approach that will work is use a virtual printer on the linux box that will print to a postscript or pdf file. The file is then sent to the windows box with the attached printer. A print server program, running under windows, that can handle the file format being used then prints the file. Here's how one person did it:

[http://www.stat.tamu.edu/~henrik/GSPSprinter/GSPSprinter.html](http://www.stat.tamu.edu/~henrik/GSPSprinter/GSPSprinter.html)

---

