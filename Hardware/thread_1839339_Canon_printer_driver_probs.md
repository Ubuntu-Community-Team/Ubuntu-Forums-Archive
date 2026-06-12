---
title: "Canon printer driver probs"
date: 2011-09-05
forum: Hardware
---

### Post by aquapunk on 2011-09-05
Hi. I'm slowly getting to love Ubuntu, but I have real problems getting my printer or scanner to work. I can live without the scanner for the moment but it would be a shame if I could not print anything.
I'm using Ubuntu 10.10 with all updates installed.

I found a driver at the Canon site for my LBP5050, with some (to me) extremely arcane installation instructions. 

I presumed I needed the debian version of CUPS and CAPT and I think I have installed them correctly.

The instructions were to then make a link with the spooler. 
This resulted in the following dialogue:

g@g-D1740:~$ /usr/sbin/lpadmin -p LBP5050 -m CNCUPSLBP5050CAPTK.ppd -v ccp://localhost:59687 –E
lpadmin: Unknown argument '–E'!

I cannot find what E was supposed to be in the first place so I am a bit lost.

I added the printer and chose the 5050 driver for it in the printer dialogue under admin, but when I try to print a test page it just registers as "processing" and system monitor shows no processes running.

Any help would be appreciated.

Thanks

---

### Post by 2F4U on 2011-09-05
Have you tried installing the printer through the CUPS web interface. The interface is accessible at

[http://localhost:631/admin](http://localhost:631/admin)

Since you already have a ppd file, installation should be relatively easy through the setup wizard of CUPS.

---

### Post by aquapunk on 2011-09-05
Thanks 2F4U. I had no idea the CUPS admin existed!
I found the ppd file and added it through the CUPS dialogue, and everything appears to be present - I can view all the printing defaults etc for the Canon. I still can't print a test page though. Same story - "processing".
The print dialogue does not list how many pages there are to print but otherwise it seems to be behaving as it should, except for actually doing anything!
Should I try waiting for more than a minute or two for something to happen?
The previous attempts still said they were processing hours later.

---

### Post by 2F4U on 2011-09-05
I have a network printer installed in CUPS and sometimes it takes extremely long until the printer starts doing its job. On some occasions, I have to press a green button on the printer (don't know how to explain it better) and only then the print starts.
Are there any led's blinking on the printer? How is it the printer connected to your computer?

---

### Post by aquapunk on 2011-09-06
No flashing LED. That happens usually when I have used the printer with the other OS-which-shall-not-be-named. There is only a cancel buttons available, and in the past with the other OS I have resorted to switching off for 10 minutes and rebooting if I had problems.

I'm connected via USB at the moment although the printer is network capable.

---

