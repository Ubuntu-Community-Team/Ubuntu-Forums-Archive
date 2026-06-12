---
title: "Canon LBP5000 problem"
date: 2008-05-25
forum: Hardware
---

### Post by Peacemonger on 2008-05-25
I installed the Canon LBP5000 color laser printer drivers according to this:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

The problem is that I can only print the Ubuntu test sheet but nothing else. This occurs with both user and root accounts. The captstatusui (run with or without sudo) says that printer is ready. The prints go to spool and disappear, but nothing comes out of the printer. Only the test sheet from printer configuration.

Any ideas?

---

### Post by silvanus2005 on 2008-05-25
Take a look there. You will find a driver provided by Canon and instructions how to install it:
[http://software.canon-europe.com/software/0028622.asp?model=](http://software.canon-europe.com/software/0028622.asp?model=)
I had a problem with those drivers - they did not work in Ubuntu, but they are working in Kubuntu 8.04 (KDE 3.5.9). And one more problem - I could not set up ccpd to start automaticaly when Kubuntu starts, so every time I start Kubuntu and want to print something I have to open console and run the command:
sudo /etc/init.d/ccpd start
By doimg that, my printer Canon LBP 3000 black&white, works fine.
I hope you will solve your problem.

---

### Post by Peacemonger on 2008-05-25
I also tried the Canon drivers with similar outcome. So it is something else (if I only knew what :) )

Peacemonger

---

### Post by pfielder on 2009-05-15
I haven't been able to get my Canon LBP 500 working on Ununtu Jaunty either. The details and options etc. are all there, but the print jobs just stay in the queue and nothing happens. Upsetting because I only bought the Canon because I saw it had a Linux driver and I had given up trying to drive my previous Kyocera laser printer FS 720 from Ubuntu since the forums were more or less agreed it couldn't be done. Some help would be welcome !

---

### Post by amicable on 2009-10-16
Bump. How do we fix this - I'm going crazy!

---

### Post by higginse on 2010-02-08
Anyone ever get it working?

---

### Post by amicable on 2010-02-10
I managed to get it working for a session or two but could not get the driver to persist between reboots. It's now an unused big white brick in the corner; I got tired of trying.

---

### Post by woodmaster on 2010-02-10
I have a different Canon: MP600: but had similar issues.  What I ended up having to do was get the .rpm files(one that said common and one that said mp600) from the Canon _Asia_ site.  I aliened both and installed with gdebi.  Then I had to remove all printers from my setup list and reinstall from none.  It outodetected my drivers and such, but set up two printers(even though there was actually only one.)  I then had to try enabling each seperately and figured out which one worked, then deleted the other.  I'd be lying if I said I fully understood how all this worked, but after some tweaks to the resulting ppd file, my printer works flawlessly.  Color, greyscale, 150-4800 dpi, etc.  Hope this helps:->

---

### Post by amicable on 2010-02-12
> **woodmaster said:**
> I have a different Canon: MP600

Interesting to see if using the rpm on the LBP5000 would work; I can't see it myself. The issues with the LBP5000 driver seem pinned down fairly well but there's no obvious solution.

[Zinovsky on Unixmen]("http://www.unixmen.com/linux-distributions/ubuntu/229-installation-canon-lbp2900-on-linux") thought he had a workable solution but it does not persist on reboots. The issue is [discussed in depth in their forum]("http://www.unixmen.com/forums/viewtopic.php?f=31&t=271") but is unresolved.

---

