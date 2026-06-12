---
title: "Printer won't finish printing!"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by BaroldGene on 2008-02-12
So I have a printer set up in Cups and I'm using Samba to share it.  I have the printer starting to print.  It loads in a page, then does nothing.  It will sit there with the job in the print queue until I delete the job from the queue.  Any suggestions?

I'm using 7.10 fully patched.

---

### Post by opscure on 2008-02-12
Is it a usb printer?  Try and remove the usb cable and reinsert it and see if it prints your queue.  If so this might be attributed to the usb ports not detecting your printer correctly.  Is it an hp printer? are you loading the firmware?  There is a lot of information that you could provide that could help us all understand your problem.

---

### Post by Fechter on 2008-02-12
What model is your printer? The first time I used my hp 610c it wiuldn't work either, but I enabled "auto-refresh device" from hplip and this solved the problem.

---

### Post by BaroldGene on 2008-02-12
It is a USB printer.  Haven't tried unplugging and replugging.  I will and see what that does.

The printer is an HP 3740 Deskjet.  I have no idea what firmware would need to be loaded.  AFAIK, the printer was autodetected and worked fine from Ubuntu directly.  But it won't seem to work from a remote share.  

I'll also look into hplip and see if that could help.

---

### Post by oldsoundguy on 2008-02-12
make doubly sure you have the correct addy for the printer entered into the remote computer for the printer.  (if it STARTS, that is correct)  
BUT is sounds like the print buffer is dumping and then not getting any more information.
NOT A CLUE as to how to address that particular issue.

---

### Post by opscure on 2008-02-18
Also, you might want to be sure you are using HPLIP and not the default HP (usb) drivers.  You can find the latest version for your distro here:
[https://launchpad.net/ubuntu/+source/hplip]("https://launchpad.net/ubuntu/+source/hplip")
or through your system update utility.
Hope this helps.

---

