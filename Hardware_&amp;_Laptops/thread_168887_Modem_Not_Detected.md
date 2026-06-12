---
title: "Modem Not Detected"
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by AnthoMacP on 2006-05-01
I've been using ubuntu for quite a while now at university and there was no issue with connectivity to the internet because I was on a highspeed connection, I set up my wireless and everything was fine. I'm now at home for the summer and in our area we can only get dialup and the trouble is, my modem is not detected. I read through some very lengthy instructions in multiple places but to no avail. I was wondering if someone could point me in the right direction for getting drivers for a BCM V.92 56K Modem and how I would go about installing them so I can connect. Not sure if any of this information is relivant but i'm on a Dell Inspiron 5150 laptop 3.06Ghz P4, Nvidia Geforce FX Go5200 etc. Thanks, hope you can suggest something :cool:

---

### Post by Peter6218 on 2006-05-01
I've got the same problem though a different modem.

In my case an AOpen 56k

Not detected.

Help, please

---

### Post by Jimmy Riddle on 2006-05-01
If it is a software modem (winmodem)  there is no quick and easy install, just follow this link :- [http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)
down load scanModem script and start from there. the wiki has a good dial up modem howto that should start you on your way.
cheers Jimmy

---

### Post by AnthoMacP on 2006-05-01
Alright. So I went to the site you suggested aswell as the ubuntu wiki on howto dialup modem and I installed the driver that scanModem recommended (SLMODEMD.gcc3.tar.gz being the tarball) and everything seemed to go fine, i followed the commands given and it said that the modem was installed "symbolic link 'dev/ttySL0' -> 'dev/pts/1' created.
modem 'modem:1' created. TTY is 'dev/pts/1'
Use 'dev/ttySL0' as modem device Ctrl+C for termination."

No error msgs so i'm assuming it all worked out fine. So I read in the readme that I require a dialer, made sense, and so I searched around to see if i had any installed. I found wvdial there and I thought this was great considering I can't actually access any repositories to get something since i don't have a connection. I attempt to run it and it says it can not detect a modem in /dev/modem/ (runs through a long list of devices it can't detect) and mentions something about wvdial.conf. Well there's no wvdial.conf file in my hd, there's wvdial.conffiles in the libraries but that's about it so i'm not sure if the packages is even installed and if it's not how i'd go about installing it and setting up a dialer to work. I then went into System>Admin>Networking and tried to activate the ppp0 device from there. It activates it, and everything seems fine, no error msgs, but when I return, it says it's deactivated. What am i doing wrong? did the driver even work? Haha i'm mildly frusterated I hope someone can help

---

### Post by Jimmy Riddle on 2006-05-01
in the tarball there should be a file called testing.txt it gives details on using wvdial, wvdialconf is part of the wvdial package it is used on the comandline by 
#sudo wvdialconf /etc/wvdial.conf 
this will scan your ports and write a config file to /etc/wvdial.

---

### Post by Jimmy Riddle on 2006-05-01
[QUOTE=Jimmy Riddle]in the tarball there should be a file called testing.txt it gives details on using wvdial, wvdialconf is part of the wvdial package it is used on the comandline by 
#sudo wvdialconf /etc/wvdial.conf 
this will scan your ports and write a config file to /etc/wvdial.[/QUOTE]
Sorry it will write a file to etc/wvdial.conf

---

