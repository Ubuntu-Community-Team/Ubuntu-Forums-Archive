---
title: "Can't print using Canon LBP6200d from ubuntu 12.04LTS 64bit"
date: 2014-03-07
forum: Hardware
---

### Post by huwwevans on 2014-03-07
Hello, I'm a big fan of ubuntu and use it for almost everything now apart from the odd computer game.  However at the moment I have to boot into windows if I want to print, I wander if you can help...

I have a Canon LBP 6200 D printer and have downloaded the drivers from the canon website.  I then installed the 64 bit Deb files (first common and then CAPT) using the ubuntu software center.  

Next I ran a whole load of commands from the terminal as listed on the cannon documentation but altering them based on the suggestions on this web page.  [https://help.ubuntu.com/community/CanonCaptDrv190?action=show&redirect=CanonCaptPrinterDriver](https://help.ubuntu.com/community/CanonCaptDrv190?action=show&redirect=CanonCaptPrinterDriver)

Now I dont' fully understand what these commands did but they didn't seem to help.  The result is the same.  The printer won't print.  

Thanks for reading and please post if you have any ideas of how to diagnose and solve this problem.

---

### Post by TheFu on 2014-03-07
I struggled with Canon printers too.  After 10 hrs of struggle, found a $50 piece of software with a 1 month free trial. It worked, but required a GUI (which bothered me).  So ... do I support the software vendor or hardware vendor?

Decided it was easier to give the printer away, buy a cheap Brother Laser for $55 and be done. That laser is still going happily using built-in drivers included with Ubuntu. Plus laser toner doesn't dry out ever. I'm on the 2nd toner in the last 5 yrs and expect it to last 3+ more years. Clearly, printing doesn't happen all that often.

---

### Post by pdc on 2014-03-08
Hi Huw

I agree the LBP needs more work than other printers; 

I think the best guide is by Sivella, who maintains the French guide

[http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp](http://doc.ubuntu-fr.org/tutoriel/installer_pilote_canon_lbp)

If you use Google translate, you can move it into your favourite language: beware though that google takes liberties when interpreting the linux commands that Sivella carefully spells out: so if you keep a copy of his guide open: in the original french you can copy and paste if need be:

my take on his guide is: for a 64bit 12.04 system

1) you need to install the ia32-libs package

then 

2)  Install the new printer in CUPS indicating which driver to use

3) tell the ccpd daemon about this printer

4) automate the recognition of the printer

so you have installed the 2.6 version of the CAPT driver? eg [http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100459601.html)

if installed, you should get it fed back to you from 

> dpkg -l | grep Canon

__________________

seems to me the command to install in CUPS would be 

> [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p LBP6200d -m CNCUPSLBP6200CAPTK.ppd -v ccp://localhost:59787 -E[/COLOR]

then to register the printer with the ccpd daemon

> [COLOR="#FF0000"]sudo /usr/sbin/ccpdadmin -p LBP6200d -o /dev/usb/lp0[/COLOR]

(If you are just connecting it to a USB port on your printer, and it is the only printer .............)

then start ccpd

> [COLOR="#FF0000"]sudo service ccpd start[/COLOR]

> [COLOR="#FF0000"]sudo service ccpd status[/COLOR]

..........is this what you did ........ the last command should give something like > [COLOR="#0000FF"]Canon Printer Daemon for CUPS: ccpd: 8956 8954[/COLOR] 

---

### Post by huwwevans on 2014-03-08
Well that did... something.  I was able to print test pages for a while but nothing else and now I can't even do that.

---

