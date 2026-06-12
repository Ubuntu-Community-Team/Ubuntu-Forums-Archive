---
title: "Printing issue driving me nuts!"
date: 2010-02-02
forum: Hardware
---

### Post by Thanh-BKK on 2010-02-02
Hello.

Please see this thread for an idea what i'm facing: 

[http://ubuntuforums.org/showthread.php?t=1391707](http://ubuntuforums.org/showthread.php?t=1391707)

I have two printers connected to my machine, that Pixma MX318 and a Fuji-Xerox DocuPrint 203 A Laser. Both via USB.

The Fuji-Xerox is shared via Samba so that all the other machines can print to it. This worked absolutely perfect BEFORE i started messing with that stupid scanner driver!!

Yesterday i found out that NEITHER of the two printers woulod PRINT anymore, neither directly from my machine nor from the network/other machines.

So today i completely removed anything to do with "CUPS" and re-installed everything, with the result that i now print on the Fuji-Xerox (both from my machine as well as from the network) and scan with the Canon, however the Canon still refuses to print!!

Drivers in use are as follows (and that worked previously):

Fuji-Xerox: Brother HL-2060 Foomatic/hpijs [EN]
Canon: Canon PIXMA MP180 - CUPS + Gutenprint v5.2.3 [EN]

I am getting this error when trying to print with the Canon:

Idle - Unable to open device "hal:///org/freedesktop/Hal/device/usb_device_4a9_1728_118787_if1_printer_noserial": Permission denied

Additionally the printing status windows states on the bottom:

Printer 'MX310-series' may not be connected

However it is connected just fine, it shows up in lsusb and i can scan with it!!

This is absolutely driving me bonkers because i need this to work. 

What can i do..??

Kind regards.....

Thanh

---

### Post by Sleepy-zz-John on 2010-03-11
Hi Thanh.   You are way ahead of me but I picked up on your post because of it's reference to your Fuji-Xerox DocuPrint 203 A Laser.  I'm also in Thailand and have one of those printers.     I'm only looking for a basic driver for mine.  
So can you actually confirm that a Brother HL-2060 Foomatic/hpijs [EN] driver works OK on your Fuji-Xerox DocuPrint 203 A?   
If so, I am curious to know how you discovered that driver was good for it.  
Many thanks!      + Sleepy J in Chiangrai

---

### Post by Thanh-BKK on 2010-03-11
Hi :)

Yes, i can confirm that said driver works for me. I am sitting in front of that computer right now (at work) and i use that printer every day.

I got that solution by simply googling for "DocuPrint 203A Ubuntu". 

My original problem - the Canon refusing to print - is still unsolved and will likely remain so as i have given up on it. I will try to convince my boss to get me an HP all-in-one because they usually work perfectly with Linux. For now if i really have to print in colour (happens rarely) i start VMware and Windows XP inside it to print from there which works perfectly, too. 

Kind regards......

Thanh

---

