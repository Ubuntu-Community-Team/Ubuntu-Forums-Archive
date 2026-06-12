---
title: "Install Printers in Ubuntu 5.10"
date: 2005-11-21
forum: General Help
---

### Post by DADDA on 2005-11-21
Hi,

How do I install my printers?

This is my printers:

Dell Laser Printer 3000cn  (Ethernet based printer)

HP Laserjet 1000 series (USB based printer)

My network is correct, i can print on my windows computer to every printer. Even the Ethernet based one.

Now the USB Printer is directly connected to my computer...


Please help me install my printers!

---

### Post by ruffneck on 2005-11-21
I haven't gotten my Dell J740 to work in linux just yet but I am doing the research. I've found this page that seems quite helpful. Check it out:
[http://linuxprinting.org/](http://linuxprinting.org/)

---

### Post by Haegin on 2005-11-21
have you found the "Printing" app under System>Administration? If not - you should search a bit harder before posting. If you have found this then I reccommend you do a google search for "the name of your printer" and "linux" (not just ubuntu).
Also check this out: [http://www.linuxprinting.org/](http://www.linuxprinting.org/) - I have never used it but it may help.
As an afterthought - check the wiki: [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

hope this helps

---

### Post by ed_d on 2005-11-21
Well, most of those show how to print if the Ubuntu is hosting the "local" printer. How does one go about printing to a printer that is connected via USB to an XP box? I have tried on my HP PSC-1400, which is supported under Ubuntu, that is connected to a WinXP box. It appears to start, but nothing prints, and we cannot delete the job in the win xp queue. Not a show stopper, but I would like to be able to kill the print job on the winxp box ( no job on the Ubuntu box btw)

---

### Post by newuser111 on 2005-11-22
check that you have the driver mapped to the correct USB port

---

### Post by HunterCo on 2005-11-22
[QUOTE=ed_d]Well, most of those show how to print if the Ubuntu is hosting the "local" printer. How does one go about printing to a printer that is connected via USB to an XP box? I have tried on my HP PSC-1400, which is supported under Ubuntu, that is connected to a WinXP box. It appears to start, but nothing prints, and we cannot delete the job in the win xp queue. Not a show stopper, but I would like to be able to kill the print job on the winxp box ( no job on the Ubuntu box btw)[/QUOTE]
A USB printer is still considered a "local" printer. I use an HP PSC1310 through a linksys USB Print Server (PSUS4) so I should be able to help you further if you give me more info, such as how you've tried installing it so far, etc.

As far as the networked printer, how is it networked? Are you using a network print server? Is the printer connected to another computer and being shared? If the former, find out the IP address of the print server and Add Printer of type Remote Printer, using the IP address of the print server. Other than that, guess we need a little more info.

---

### Post by ed_d on 2005-11-22
LIke I said, its attached to a WInXP box. I have tried via the ip address of the winxp box, even gone as far as adding the ip to my /etc/hosts to make it easier.

Still no joy. What else do you need?

---

### Post by tim15856 on 2005-11-22
Look to this post: [http://www.ubuntuforums.org/archive/index.php/t-27736.html](http://www.ubuntuforums.org/archive/index.php/t-27736.html)

---

