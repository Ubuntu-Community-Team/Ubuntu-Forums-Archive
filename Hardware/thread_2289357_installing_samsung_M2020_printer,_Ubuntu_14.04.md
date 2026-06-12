---
title: "installing samsung M2020 printer, Ubuntu 14.04"
date: 2015-08-03
forum: Hardware
---

### Post by virtdave@mcn.org on 2015-08-03
I have been having difficulty installing this printer.  I have downloaded the 'Universal Linux Driver' from the Samsung website, unpacked it, and gotten to the appropriate place to start the installation ('david@david-desktop:~/Desktop/uld') with sudo ./install.sh in the command line.  The installation proceeds, but after all the legal jargon from Samsung, just after the message '**** Do you agree ? [y/n]', before I can respond 'y' (immediately) I get the message '**** Terminated by user', followed by about 20 identical lines showing where I put the appropriate driver installation file ('david@david-desktop:~/Desktop/uld').  Any ideas?

---

### Post by dino99 on 2015-08-03
i propose you purge the package(s) you have installed from Samsung, then redo the installation as explained below

[http://askubuntu.com/questions/645681/samsung-m2020-on-ubuntu](http://askubuntu.com/questions/645681/samsung-m2020-on-ubuntu)

---

### Post by mastablasta on 2015-08-04
or read this and add a PPA: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

---

### Post by kurt18947 on 2015-08-04
That **is** a bit of a bother, I've had the same thing happen. The trick I found was to scroll pretty rapidly through about section 6 then slow down. If keyboard commands are ahead of the display, a 'continue' or 'next' command will be entered at the "do you agree" line. The default seems to be "no" so the installer aborts. There are large sections then the last couple are pretty small so it's easy to 'overshoot'. It's been a while since I installed the Samsung driver so my recall may be faulty. I seem to recall having to run the printer and scanner installs separately. I also found that for the Samsung machine I have -- SL-M2870FW -- there seems to be a driver included by default in Ubuntu. For grins I started system-config-printer before installing the Samsung driver  then searched for network printer. The Samsung was found and a driver listed. I installed that and it printed. I didn't try scanning so I don't know if the scanner software was included.

---

