---
title: "HP 1022 laserjet printer stuck on paused"
date: 2012-02-13
forum: Hardware
---

### Post by a.v.l on 2012-02-13
This HP laserjet 1022 printer has worked perfectly in previous Ubuntu versions and installed perfectly and worked for around thirty sheets of printed text since installing Ubuntu 11.10. 

Now it refuses to print at all. There are six print jobs waiting in the queue which I'm unable to delete. The printer is stuck on "Paused" and I'm unable to do anything to get it to work. Would anyone be able to help please.

---

### Post by GPilot on 2012-02-13
> **a.v.l said:**
> This HP laserjet 1022 printer has worked perfectly in previous Ubuntu versions and installed perfectly and worked for around thirty sheets of printed text since installing Ubuntu 11.10. 

Now it refuses to print at all. There are six print jobs waiting in the queue which I'm unable to delete. The printer is stuck on "Paused" and I'm unable to do anything to get it to work. Would anyone be able to help please.

Have you tried reinstalling HPLIP?

---

### Post by a.v.l on 2012-02-13
> **GPilot said:**
> Have you tried reinstalling HPLIP?

Yes I reistall HPlip to the latest version 3.12.2 after installing 11.10 to allow an HP wireless all in one printer to work. This wireless printer is still working correctly, its just the HP laserjet which has decided to stick on paused. Oddly it worked perfectly one minute and not the next.

---

### Post by lechien73 on 2012-02-13
I had this with my HP LaserJet before - and it seems CUPS had somehow paused the printer.

I fixed it by opening [http://localhost:631](http://localhost:631), selecting the **Printers** tab, clicking on the printer name, and then choosing **Resume Printer** from the **Maintenance** pull-down menu.

---

### Post by holycow131415 on 2012-02-13
Maybe if you delete the printer and readd it.

---

### Post by a.v.l on 2012-02-13
> **holycow131415 said:**
> Maybe if you delete the printer and readd it.

Yes I've just deleted the laserjet printer and rebooted the pc and nothing. PC did not recognise the usb HP 1022 printer and there are no options to install new printer that I can find. 

My other HP wireless printer is working normally still although it would not install with the version of HPlip which came with 11.10.  So I installed the latest version of HPlip which brought both printers to life-until today, now only the wireless printer works. 

So to recap. I am unable to install my usb HP laserjet 1022 and can find no means of doing so, no button to install new printer and printer is not seen by PC

---

### Post by Closetheloop on 2012-12-04
Yes I encountered this Paused Printer problem for the first time today.

My solution was to go System Settings - Printing - Printer Properties - Policies - and then ensure that State Enabled is checked ON.

For some reason my printer State Enabled has become checked off...

I now have solved the problem :)

Good Luck

---

### Post by llazarte on 2013-03-04
> **lechien73 said:**
> I had this with my HP LaserJet before - and it seems CUPS had somehow paused the printer.

I fixed it by opening [http://localhost:631](http://localhost:631), selecting the **Printers** tab, clicking on the printer name, and then choosing **Resume Printer** from the **Maintenance** pull-down menu.

Thanks a lot! I recovered access to my printers by accessing CUPS with your suggestion.

---

### Post by Nalin Khurb on 2014-02-18
> **lechien73 said:**
> I had this with my HP LaserJet before - and it seems CUPS had somehow paused the printer.

I fixed it by opening [http://localhost:631](http://localhost:631), selecting the **Printers** tab, clicking on the printer name, and then choosing **Resume Printer** from the **Maintenance** pull-down menu.

Thanks, it fixed my issue too. My hp laserjet 1022 was not printing jobs and just stopped them instead. :P=d>

---

### Post by cacs on 2014-03-15
Hi. 
Tyvm for your tip, it's just what I needed to know! :)
C.S.

---

### Post by fx_viallon on 2014-03-25
> **llazarte said:**
> Thanks a lot! I recovered access to my printers by accessing CUPS with your suggestion.

it did the job for me, too. Thanks a lot!

---

