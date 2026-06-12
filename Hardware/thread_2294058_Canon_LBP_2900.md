---
title: "Canon LBP 2900"
date: 2015-09-09
forum: Hardware
---

### Post by krishnan t s on 2015-09-09
Sorry if i'm posting the wrong forum. Feel free to change it to the right one if necessary.

I have a 32-bit HP Compaq desktop and a Canon LBP 2900 laserjet printer. I have configured it using [this]("http://askubuntu.com/questions/457774/driver-canon-lbp-2900") link  and it works well on ubuntu 14.04.3. I have a couple of questions regarding the printer:


[LIST=1]
[*] On windows, when the printer runs out of paper during print, it flashes a small orange light and asks us to load paper. After loading the paper, pressing the button on the printer glowing orange resumes printing.In ubuntu, on pressing the same button, nothing happens unless i restart the ccpd service and even then sometimes the printer does not work. 
[*]The settings are not saved on reboot. i have to run the following 2 commands to make the printer work again: 
[/LIST]
                   sudo pkill -9 -x ccpd
                   sudo /etc/init.d/ccpd start.
        Is there anyway i can auto-execute these commands on boot? if so, can u give a step-by-step way to do it?

Thanks in advance for your reply :)

---

### Post by krishnan t s on 2015-09-12
Update:
I tried to print a document from the web. It wouldn't print. Saved it as PDF and tried to print. It wouldn't print. But it prints test pages which is pretty useless to pretty much anyone :P

---

### Post by krishnan t s on 2015-09-21
Haven't had any reply so far. Just came to inform that the printer works again. Found some loose connection. I just need one small help.
I need to run the above 2 commands on startup every-time to get printing working. I was planning to set up a cron job to do it but the man page is too confusing. Could someone guide me to do it or give a better solution to do it??

---

### Post by krishnan t s on 2015-10-31
Anyone?? I'd like to run only those 2 sudo commands on startup :)

---

