---
title: "Linux modem ISP dial-up help"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by georgewa on 2006-03-12
For the past week, I have been trying to install a linux modem (us robotics 5610B) for ISP dial-up and haven't succeeded yet, and need help !

This hardware linux modem works and installs without a problem/works with my ISP with RH 7.3.

Current setup: FIC AN11 mb( 266A) , AMD Athlon xp1800, 512 memory, 200mb hd, Ubuntu 5.10 desktop from free cd

I've tried to get things rolling by going thru the Dialup Modem-howto but these are the problems I have encountered:

When I look at the system devices, I see it lists the 5610 serial modem.

(1) pppconfig - sudo pppconfig was run and everything went fine. I found out the serial port location by running wvdial, which said the modem was recognized at /dev/ttyS14, so that was what I entered in the config.

When I type pon, I get the error message that the isp phone no, usr name and pw were not entered , but when I do a gedit on pppconfig the info is all there that I had to enter separately from the first config.

(2) wvdial.conf - this is completed but when I type sudo wvdial, I get the following error message - /usr/sbin/pppd infile /etc/ppp/peers/provider unrecognized option /dev/modem

When I look at the file "provider" with gedit , I see nothing in the file but remarks. I tried copying everything in pppconfig to "provider" and that did not help. 

(3) administration / network - I didn't try the isp connection that route. It was noticed that the first thing that came up when that was selected was the message modem ppp0 not installed and it showed /dev/modem as the location. I tried changing it to the known location of /dev/ttyS14 or to nothing and it did not help.

Suggestions???

Thank you.

Walter

---

