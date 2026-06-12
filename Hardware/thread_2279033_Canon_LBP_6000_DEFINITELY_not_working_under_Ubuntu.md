---
title: "Canon LBP 6000 DEFINITELY not working under Ubuntu 14.04/15.04"
date: 2015-05-20
forum: Hardware
---

### Post by fabcattani on 2015-05-20
Read everything about this on every forum found.. it just doesn't work

---

### Post by Vladlenin5000 on 2015-05-20
Hi and welcome.

[http://askubuntu.com/questions/473728/making-canon-lbp6000-printer-work-under-ubuntu-14-04-64-bit](http://askubuntu.com/questions/473728/making-canon-lbp6000-printer-work-under-ubuntu-14-04-64-bit)
[http://askubuntu.com/questions/463289/cant-get-my-canon-lbp-printer-to-run-under-ubuntu-14-04](http://askubuntu.com/questions/463289/cant-get-my-canon-lbp-printer-to-run-under-ubuntu-14-04)

---

### Post by pdc on 2015-05-21
Hi fabcattani;

welcome to the forums; can you tell us please if you had used a 32bit system for the ubuntu versions you evaluated? 

The LBP6000 needs Canon's CAPT driver; do you agree? 

> Read everything about this on every forum found

but can you tell us what you did do please?

I think there are 4 steps:

1) connection
2) drivers
3) Register the printer (PPD) with the print spooler ... as with every printer
4) the extra step: Register the printer in the ccpd daemon setup file.............and restart the cppd daemon .................

---

### Post by Bucky Ball on 2015-05-21
> **fabcattani said:**
> Read everything about this on every forum found.. it just doesn't work

Welcome. Did you want support or are you just saying? If you'd like support, please give all info requested by helpers (and anything you've tried so far, see the third link in my signature for some tips). If you're just saying, I'll move this post to the appropriate forum area.

Good luck either way. ;)

---

### Post by fabcattani on 2015-06-08
459
- Ubuntu 15.04 32bit
- drivers properly installed
- followed ANY hint found on this and other forums about this printer

it's like printer is not connected to the PC..477

---

### Post by pdc on 2015-06-08
hi fabcattini;

welcome back to the forums; 

you say ................. >  drivers properly installed .............. but please tell us what you did ............which guide did you follow ..... 

if you open a terminal and paste in this command ```
/usr/sbin/lpinfo -v
``` can you please copy the results and paste them back here please ...............

---

### Post by Maximo Soria on 2015-06-24
Hello everybody, I have exactly the same problem, I've tried many alternatives and nothing works, after running /usr/sbin/lpinfo -v this is what I get:

direct hp
network ipp14                                                                                                                                                                     
network lpd
network socket
network ipps
network https
network ipp
network http
direct usb://Canon/LBP6000/LBP6018?serial=0000B2A86LLe
direct hpfax

Any help???

---

### Post by fabcattani on 2015-07-07
B590:/sbin$ lpinfo -v
direct ccp
file cups-pdf:/
network ipp
network ipps
network http
network https
network ipp14
network lpd
network socket
direct hp
direct usb://Canon/LBP6000/LBP6018?serial=0000B4B5NGgJ
network smb
direct hpfax


208
NO WAY TO MAKE IT WORK!

---

### Post by Bucky Ball on 2015-07-07
Have you tried [here]("https://help.ubuntu.com/community/CanonCaptDrv190#Ubuntu_14.04_Install"), [here]("http://askubuntu.com/questions/174474/installing-canon-lbp6000-in-ubuntu-12-04") or [here]("https://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/")?

While I understand your frustration, shouting in capital letters about how there's no way to make a printer work when others appear, with some jumping through hoops, to have it working, is generally just going put people off trying to help. You are unable to get it to work, but the printer, it appears, does indeed work with Ubuntu.

Better to try the first link and see how you go then post back with details when you get stuck. Posting "Read everything about this on every forum found.. it just doesn't work," won't get you far. You provide no links to all the things you've tried or where you're at with it. No error messages and nothing to go on for helpers. Suggest you read the third link in my signature for future threads.

Good luck with it.

---

