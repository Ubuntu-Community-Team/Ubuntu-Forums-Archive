---
title: "URGENT: HP Printer not working"
date: 2013-08-23
forum: Hardware
---

### Post by Jonny87 on 2013-08-23
I have an HP Diskjet printer, the detalis according to cups are.

[TABLE]
[TR]
[TH]Description:
[/TH]
[TD]HP Deskjet 3070 B611 series[/TD]
[/TR]
 [TR]
[TH]Location:
[/TH]
[TD]Office[/TD]
[/TR]
 [TR]
[TH]Driver:
[/TH]
[TD]HP Deskjet 3070 b611 Series, hpcups 3.13.8 (color, 2-sided printing)
[/TD]
[/TR]
[TR]
[TH]Connection:
[/TH]
[TD]hp:/usb/Deskjet_3070_B611_series?serial=CN23P6829Y05MQ[/TD]
[/TR]
[/TABLE]

When I try to print nothing happens. The print que say that the job has been stopped and reprinting it doesn't work. The "State" say;
[I]"/usr/lib/cups/filter/hpcups failed"

[/I]I've trie searching for answers and tried any possible I could find. I have tried removing the printer and re-adding it (multiple time). I've tried reinsatll HPLIP with the latest version. Tried turning the printer on and off and have restarted the comp as well. Still end up with the same result.

Running Ubuntu 12.04

Please help as this is urgent as I need it going to do business.

---

### Post by Bucky Ball on 2013-08-23
*Thread moved to **Hardware**.*

You need to install HPLip (from Software Centre or Synaptics). Most HP printers are very well supported. Install HPLip, restart and see if that works. Go to the HP website and find the Linux driver for your device. There should be specific instructions about how to install your device there. Read them and the user manual (thoroughly, if you haven't ten times already!).

Once HPLip and the correct driver are installed, go to Printer and 'Add Printer'. Add your printer. If it is wireless, click 'Network Printer' and wait til it's picked up.

I'm repeating these steps as this would be the course of action. If you delete all printers, reboot and start from the beginning then let us know what happens would be good. You haven't mentioned whether this is USB or wireless or how you're connecting with it. It says USB above but is this correct?

---

### Post by Jonny87 on 2013-08-23
> **Bucky Ball said:**
> *Thread moved to **Hardware**.*

You need to install HPLip (from Software Centre or Synaptics). Most HP printers are very well supported. Install HPLip, restart and see if that works. Go to the HP website and find the Linux driver for your device. There should be specific instructions about how to install your device there. Read them and the user manual (thoroughly, if you haven't ten times already!).

Once HPLip and the correct driver are installed, go to Printer and 'Add Printer'. Add your printer. If it is wireless, click 'Network Printer' and wait til it's picked up.

I'm repeating these steps as this would be the course of action. If you delete all printers, reboot and start from the beginning then let us know what happens would be good. You haven't mentioned whether this is USB or wireless or how you're connecting with it. It says USB above but is this correct?

Sorry yea its USB. It has a wireless ability but I'm connected via usb. I did have the standard HPLIP installed from the Ubuntu repositories and it was still doing the same thing so aoung other things I thought I'd try upgrading it to the latest version from the website. This was suggested on a page I found with about the same or similar issue. 
As suggested I will try it all again from scratch.

---

### Post by Jonny87 on 2013-08-23
OK so after a couple more attempts I tried a test page this last time around and found that it worked. So I went back to inkscape and tried to print andgot the same result as earlier. So I tried saving to a PDF and printing from Okular, worked fine. So it seems that issue is perhaps with Inkscape and not cups or hplip. So I've probably wasted most of the day for nothing.
Yes, I am feeling realy fustrated right now... ](*,)

---

### Post by Irihapeti on 2013-08-24
I've had the same problem trying to print from Inkscape in 12.04, with a slightly different printer - HP Officejet 5610. No other programs misbehave like that.

I might try in 13.10 and see if that makes any difference.

---

