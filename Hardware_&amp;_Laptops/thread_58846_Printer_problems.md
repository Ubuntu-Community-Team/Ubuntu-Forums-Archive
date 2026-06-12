---
title: "Printer problems"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by Chris Cromer on 2005-08-21
Alright, I have a Lexmark Z11 printer with color ink. I can't for the life of me get it to work in ububtu. I tried printing test pages but nothing every happens.

Now before you tell me to go to the linux printing site, I have already gone there, found my printer, installed the driver, and it still would not work.

Any advice on how to get it to work would be helpfull.

---

### Post by humanity_to_others on 2005-08-21
[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z11](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-Z11)

---

### Post by Chris Cromer on 2005-08-21
I have already been to that site and it hasn't helped me one bit. I tried all 3 driver they have listed, and none of them worked, still nothing would print.

---

### Post by linuxdream on 2005-08-21
Any other details like is it USB, log messages, proc info?

---

### Post by Chris Cromer on 2005-08-22
It's connected through my only parallel port on a dell inspiron 2650 laptop. As for log messages and proc info, no idea what that is. How would I find it out?

---

### Post by az on 2005-08-22
[QUOTE=Chris Cromer]It's connected through my only parallel port on a dell inspiron 2650 laptop. As for log messages and proc info, no idea what that is. How would I find it out?[/QUOTE]


What are your parallel port settings in BIOS?

---

### Post by Chris Cromer on 2005-08-22
Parallel Port: Customized
Mode: ECP
Base I/O Address: 378
Interupt: IRQ7
DMA Channel: DMA1

Any other info you need?

---

### Post by David Haas on 2005-08-22
Chris--I'm curious to know why you didn't use the "driver" (PPD file) within Ubuntu, instead of downloading it (?) I see the PPD file in the Lexmark directory at "/usr/share/cups/model/foomatic-ppds/Lexmark". It's "Lexmark-Z11-lz11.ppd.gz". After installing (selecting) the PPD file, Linux places an unzipped copy in /etc/cups/ppd. Do you have such a file in this directory now? It seems to me that it's worthwhile delecting your printer in the Gnome Print Manager(System>Administration>Printing) and then beginning fresh by selecting your printer in this manager and then selecting the driver/PPD file by clicking through the above directories to find the file.
David

---

### Post by Chris Cromer on 2005-08-23
Because I didn't know there was a driver within Ubuntu. I am a first time linux user(except for when dealing with permissions remotely via ftp for apache, php, and perl scripts). And a first time ubuntu user as well.

Actually I noticed that when I installed a driver it was put into /usr/share/cups/model/ is it put into /etc/cups/ppd/ as well?

I tried fresh with the driver in ubuntu, still no luck. Nothing happens.

---

### Post by David Haas on 2005-08-23
Chris--Apparently, some extra steps are needed to install the Lexmark Z11. Go to the following Forum note that I found in the Forum search engine: <http://www.ubuntuforums.org/showthread.php?t=30742&highlight=Lexmark+Z11+printer>
It describes how another user installed this printer. If you have questions about the steps described, then you could get help again in this forum. I hope this helps.
David

---

### Post by Chris Cromer on 2005-08-23
Sweet. Thank you so much. I am getting closer and closer to leaving windows completely. :)

---

### Post by yellowstar5 on 2006-05-31
The lz11-v2 driver works fine for me with a black and white cartridge but a colour one gives an array of yellow, magenta, and green stripes.

---

