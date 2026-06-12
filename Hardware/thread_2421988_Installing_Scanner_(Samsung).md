---
title: "Installing Scanner (Samsung)"
date: 2019-06-30
forum: Hardware
---

### Post by linuxo2 on 2019-06-30
Hello!
I am a new Linux-User and have trouble installing drivers. I use Ubuntu 18.04.2 LTS and a Samsung Xpress M2885 FW printer/scanner which should work perfectly on Linux (see [https://www.openprinting.org/printer/Samsung/Samsung-M288x](https://www.openprinting.org/printer/Samsung/Samsung-M288x)).It is connected to the computer via USB-cable. 
I downloaded the drivers from Samsung’s website ([https://support.hp.com/nz-en/drivers/selfservice/samsung-xpress-sl-m2880-laser-multifunction-printer-series/16462717](https://support.hp.com/nz-en/drivers/selfservice/samsung-xpress-sl-m2880-laser-multifunction-printer-series/16462717)), installed them successfully with “sudo ./install.sh” and executed“system-config-printer”. Then I completed set-up of the printer in Printers / Additional Printer Settings. Now printing works perfectly. 
However, I am missing both the scanner and an interface to communicate with it from the computer (such as Easy Printer Manager).
Your help would be highly appreciated.
Thanks and regards,
linuxo

---

### Post by CatKiller on 2019-06-30
Scanning happens through a different method than printing: most printers don't have a scanner; most scanners don't have a printer. Printing happens through a mechanism called CUPS, and scanning happens through a mechanism called SANE.

There's an application called simple-scan, which I always found fine to use, or you can scan directly in the Gimp. I'm sure there are other front ends, too. The part that communicates with the scanner is called the back end.

---

### Post by brian_p on 2019-06-30
See

[https://ubuntuforums.org/showthread.php?t=2421815](https://ubuntuforums.org/showthread.php?t=2421815)

The OP in that post might eventually see a way of commenting on the proposed solution. But don't hold your breath.

---

### Post by brian_p on 2019-07-02
First a direct request is made of a user. Then a hint is given to a second user. No response in either case. Deary me!

---

### Post by kurt18947 on 2019-07-02
I have an earlier version of that Samsung. I didn't have success running the install.sh script. I was successful running the install-scanner.sh and install-printer.sh though.  I'm not sure why installing the components separately work while installing both at one time didn't work but that was my experience.

---

### Post by linuxo2 on 2019-07-09
@ Brian: Sorry for my late reply. I recently completed my first professional assignment on Linux with Writer and Calc - it was stressful but worked out pretty well. I am now working through The Linux Command Line book to make some more progress. The scanner remains a problem as that Samsung model is not supported by SANE.

---

### Post by linuxo2 on 2019-07-09
@ Kurt18947: I ran the install-scanner.sh separately again but did not get any result, i.e. I could not access / find the scanner anywhere on the computer. Kindly let me know what you did after running the install-scanner.sh. Is your Samsung model supported by SANE and do you operate the scanner via SimpleScan? Regards, L.

---

### Post by CatKiller on 2019-07-09
There have been [reports](https://askubuntu.com/a/1033127) that those scripts put the SANE stuff in the wrong place, and correcting that makes the scanner work again.

---

### Post by mastablasta on 2019-07-10
does this help? : [https://www.bchemnet.com/suldr/](https://www.bchemnet.com/suldr/)

It's the old driver.

also HP is taking care of Samsung printers now (not all though). so most drivers should be in kernel or hplip.

if nothing else the linked website provides a lot of good information and some troubleshooting options for scanning.

edit: i have Samsung SCX printer and i had to use this site & drivers before (on 14.04) to be able to print & scan. it even worked on Linux PC, while printer was on windows XP. but now driver came with the OS. the issue with linux drivers before was that packaged drivers on Samsung CD or website actually had osme errors in them and didn't work properly. the user on the linked site fixed them and then offered correct and working drivers as PPA.

---

