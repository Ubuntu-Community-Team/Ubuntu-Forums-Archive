---
title: "iClicker.exe, wine, USB, might have to go back to XP"
date: 2008-10-03
forum: General Help
---

### Post by dr_d12 on 2008-10-03
Hi guys,

In the off chance that there is a fix for my problem I thought I'd ask for comments.

I'm using my laptop for presentations in college classes and I use a radio frequency classroom response system called an iClicker.  I have a receiver that plugs into the USB port - it collects responses from student remotes and sends them to the iClicker program (iClicker.exe). 

I added the missing DLLs and have iClicker.exe running under Wine, but it can't talk to the receiver through the USB port (it gives an error that the receiver is not plugged in to USB). Before I trash the idea of running linux in the classroom, do I need to do something like map the USB connection for Wine?

The iClicker program can run from a USB drive - it doesn't need to be installed so I don't think XP needed a driver for the base.

The only other information I found about this (I'm sure very uncommon) problem is on the following website:

[http://ml.osdir.com/python.pyusb.user/2008-06/msg00000.html](http://ml.osdir.com/python.pyusb.user/2008-06/msg00000.html)

What do you think? I hate to have to pull out the XP disk...

Thanks, Dave

---

### Post by cpbl on 2008-11-04
Hi. I'm in the same boat. I will be using iClicker next term with Linux. I'm at UBC in Canada.

I've had a quick look at using VirtualBox  (a virtual machine) rather than Wine. ie, if you're installing XP, do it under VirtualBox rather than switching over completely.
 There it sounds like one needs to do a trick to get VirtualBox permission to see USB, so maybe the same trick is stopping wine?

I'd like to keep up to date on your efforts/success -- I'm keeping notes on an "iClicker with Linux" web page. (though iClicker says they'll support Linux by July 2009.)

Best,
Chris

---

### Post by cpbl on 2008-11-14
I have the iClicker working under VirtualBox under Ubuntu. 
I've made notes at 
[http://grad.econ.ubc.ca/cpbl/web/software/iClicker.html](http://grad.econ.ubc.ca/cpbl/web/software/iClicker.html)

I'm not sure it's flawlessly smooth yet.

Wine seems a dead end, as there is no USB support under Wine.

Chris

---

### Post by dr_d12 on 2008-11-27
Thanks Chris, after finals I'll try to get this running and post results here.

---

