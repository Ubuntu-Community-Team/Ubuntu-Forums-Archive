---
title: "Gateway SOLO 5300 - MODEM TROUBLE"
date: 2006-06-26
forum: Hardware &amp; Laptops
---

### Post by SirShaggy on 2006-06-26
I am very new to Linux. Maybe 2 weeks. Please be patient with me and FULLY explain steps.

OK, I have managed to figure out that I have a ltmodem in my laptop. It is an Agere Systems WinModem and under lspci -n, it was identified as 11c1:0448. I have found lots of information on google and tried to figure this all out. I DONT UNDERSTAND!

First, I am not trying to use the dial up part of a modem, I want to connect by ethernet to my external ADSL modem. Ubuntu didn't see an ethernet connection and I am trying to set one up. Do I need to try to get the Agere WinModem working to do this?

Second, I used a different computer to download ltmodem-2.6-alk-8, I put the downloaded file onto a CD and then put it onto the desktop of my laptop. That is as far as I can understand. :( 

Where do I move it to?
how do I install it?
Any suggestion or ideas?

Please help me out if you have time. I really do need step by step instructions and don't wish to waste anyone's time. I would just like to be able to use this old laptop once again, It has a lot of life left and I don't have the money to buy a new one.

Shaggy

---

### Post by SirShaggy on 2006-06-26
On this laptop, the modem and the Ethernet controller are a mini PCI card. They are one in the same. You must configure the 56K modem to be able to use the ethernet port! Weird huh? Anyway, I did get it working, just thought I'd post the info.

---

### Post by nicksmyname on 2007-06-17
Hi Sir Shaggy,
I am new to Ubuntu aswell and have similar problems getting the modem running on a Solo 5300.  Can you post the steps you took to solve the problem?
Thanks,
NicksMyName

---

