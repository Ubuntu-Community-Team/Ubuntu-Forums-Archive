---
title: "56k modem on Gutsy"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by archman on 2008-02-20
Hi, I have hp nx6310 and i need someone to identify my modem and tell me what drivers I need.
I attached ModemData.txt
The [email]Discuss@Linmodems.org[/email] doesn't work...

Seems like it's some audio+modem chipset...

Thanks !

---

### Post by RxRated on 2008-02-20
Looks like a smartlink modem.  Go to Synaptic package manager and  install the sl modem daemon package.  You'll also need a dialup manager like kppp or wvdial.  I use kppp on my laptop with a smartlink modem and it works well enough.

Steve

---

### Post by AnonCat on 2008-02-20
*deleted*

---

### Post by archman on 2008-02-21
Thanks for the help. I got slmodemd installed. Already had wvdial...
I think it works...I momentally can't test the connection 'cuz I don't have telephone here, but when I start wvdial it breaks on when checking for dialtone. So I think that's it !

Thanks for the help !

archer

---

### Post by archman on 2008-04-04
cd to slmodemd source extracted
chmod a+x slmodemd
cp slmodemd /usr/sbin
find /usr -name slmodemd        ---should only 1 new added
modprobe snd-intel8x0m					
slmodemd --alsa -c CTR21EUROPE hw:0,6			   -leave terminal, open new and:
wvdial to dialout   (edit /etc/wvdial.conf for accounts)

wvdial.conf example:

[Dialer Defaults]
Phone = 0xxxxxxxxx
Username =xxx
Password = xxx
New PPPD = yes
Carrier Check = no
#Stupid Mode = yes

---

