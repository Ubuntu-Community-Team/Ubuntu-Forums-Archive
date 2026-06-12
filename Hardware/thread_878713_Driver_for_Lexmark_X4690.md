---
title: "Driver for Lexmark X4690?"
date: 2008-08-03
forum: Hardware
---

### Post by gianhut on 2008-08-03
I just bought a new printer an apparently, Ubuntu 8 is not recognizing it.
I've try the [HOWTO: Lexmark Printers...]("http://ubuntuforums.org/showthread.php?t=49714") and it didn't work.
I really don't wanna switch back to Windows =(

Please help! Thanks

---

### Post by zachthejones on 2008-08-19
Yeah man, I'm sorry. I just got the same printer and I can't find any drivers for it to work. It seems that Lexmark is not very linux friendly...I'm probably going to return my printer and get one that's more compatible.

---

### Post by NoBugs! on 2009-01-03
Lexmark drivers are available here: [http://downloads.lexmark.com/perl/downloads/downloads.cgi](http://downloads.lexmark.com/perl/downloads/downloads.cgi)
There is only a Mac & Windows version, but since Mac os uses the same "cups" printing system, shouldn't there be some way to convert Mac os drivers?

---

### Post by 2hot6ft2 on 2009-01-03
Try looking here. [http://ubuntuforums.org/showthread.php?t=49714&highlight=Lexmark](http://ubuntuforums.org/showthread.php?t=49714&highlight=Lexmark) and good luck.

---

### Post by NoBugs! on 2009-01-12
> **2hot6ft2 said:**
> Try looking here. [http://ubuntuforums.org/showthread.php?t=49714&highlight=Lexmark](http://ubuntuforums.org/showthread.php?t=49714&highlight=Lexmark) and good luck.

That didn't work for me either, I tried z600 and z700 drivers.

Taking it back would be a good idea, when it does work, this printer seems to chew paper as it goes through:(

---

### Post by Bablefish on 2009-01-12
I hate to tell you there are NO Linux drivers for anything Lexmark. I know I tried everywhere...and I do mean everywhere. I finally had to give up and buy an HP printer

---

### Post by NoBugs! on 2009-01-14
There aren't drivers for the *newer* lexmark printers. 
Some of those older printers have been tested to work with old lexmark linux drivers (z600,z700). See here:
[http://openprinting.org/printer_list.cgi?make=Lexmark](http://openprinting.org/printer_list.cgi?make=Lexmark)

---

### Post by Sef on 2009-01-14
> I hate to tell you there are NO Linux drivers for anything Lexmark. I know I tried everywhere...and I do mean everywhere. I finally had to give up and buy an HP printer

Not true.  Usually for business computers (Optima), there are Linux drivers.   For comsumer printers, there are not.

---

### Post by merkourios on 2009-02-16
well,the only solution is to make a virtual XP installation. The printer works perfectly for me now. Used the Sun xVM VIRTUAL BOX.
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Bablefish on 2009-02-16
I had a Lexmark printer, and I looked for 6 months for a Linux driver and could not find on period. I finally had to buy a HP printer, as it seems to be the only widely supported printer on Linux.

---

### Post by nachfolger on 2009-11-13
I'm having the same problem with the X4690 - i can't seem to find any drivers that will work either.  I think the virtual box is the only option until i can afford a new printer.

---

### Post by Graham_191 on 2010-03-31
The Lexmark site apears as if they have provided linux support for the x4690

[http://support.lexmark.com/index?page=recommendedDownloads&locale=en&productCode=LEXMARK_X4690&segment=DOWNLOAD&userlocale=EN_US#1](http://support.lexmark.com/index?page=recommendedDownloads&locale=en&productCode=LEXMARK_X4690&segment=DOWNLOAD&userlocale=EN_US#1)

hope that is useful for anyone still

---

### Post by tchepaim on 2010-04-17
This printer works for me, now also in Wi-fi mode. Thanks to Graham-191 that shared the link to linux drivers ([http://support.lexmark.com/index?page=recommendedDownloads&locale=en&productCode=LEXMARK_X4690&segment=DOWNLOAD&userlocale=EN_US#1](http://support.lexmark.com/index?page=recommendedDownloads&locale=en&productCode=LEXMARK_X4690&segment=DOWNLOAD&userlocale=EN_US#1)). 

But I have some issue with wi-fi setup. In this part of configuration, I have to use another OS in my network, only to put my WEP key to printer (sorry, at this moment the only option for me). Back to Ubuntu, I add a Network Printer > App/Socket > Put the host address like (192.168.1.xxx) > Nothing in Port Number and Voilá! It works.

Now I have 2 computers with Ubuntu printing via Wi-fi.
Hope this help. Good Luck.

---

### Post by rorkimaru on 2010-04-29
Hey, I was just trying to install the drivers from the lexmark site and I got the installer to download, it runs fine but when it asks for root access and for me to input the password it claims it's wrong even though I'm entering the correct password. Its the same one I use for synaptic package manager and the software center right?

Using 10.04 and the installer is for 10.04

---

### Post by wbar2 on 2010-05-01
> **rorkimaru said:**
> Hey, I was just trying to install the drivers from the lexmark site and I got the installer to download, it runs fine but when it asks for root access and for me to input the password it claims it's wrong even though I'm entering the correct password. Its the same one I use for synaptic package manager and the software center right?

Using 10.04 and the installer is for 10.04

I'm not sure what the problem is, but here's a solution under number 2 in this tutorial: [http://ubuntuforums.org/showthread.php?t=1444847](http://ubuntuforums.org/showthread.php?t=1444847)

---

### Post by Graham_191 on 2010-05-30
> **wbar2 said:**
> I'm not sure what the problem is, but here's a solution under number 2 in this tutorial: [http://ubuntuforums.org/showthread.php?t=1444847](http://ubuntuforums.org/showthread.php?t=1444847)
This worked for me, hopefuly it will work for you too. If you run nautilus with root privlages. Just type "sudo nautilus" into the terminal and then navigate to the intaller and run it.
 hope this works

---

### Post by Fromanator on 2010-07-09
Well Lexmark finally has Deb and RPM packages for this printer, I actually complained to them via email about how they already had CUPS implemented for OSX, and it wouldn't be too hard to write a driver for linux. To my suprise they did pass it on and several months later they had drivers for debian and fedora based linux. Anyway the current driver listed for this printer doesn't support wifi printing out of the box. So I received a work around from Lexmark.
1. Make sure the printer is on and connected to your wireless network (green light).
2. Make sure you have the driver listed for this [model]("http://support.lexmark.com/index?page=content&productCode=LEXMARK_X4690&actp=PRODUCT&id=DR20523&segment=DOWNLOAD&userlocale=EN_US&locale=en").
3.  Install any 2009 Linux printer driver (make sure the driver is compatible with the linux version installed on the computer) – The purpose of installing any 2009 printer driver is to get lxnet which will be necessary to make wireless printing possible. Currently, the 2008 inkjet printers don't have the lxnet file. Here's the link for the  [driver]("http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-09-driver-1.5-1.i386.deb.sh.tar.gz").
4. Copy lxnet from /usr/lexinkjet/lxk09/bin/ to /usr/lexinkjet/08zero/bin. To do that just go to terminal and type:

cp /usr/lexinkjet/lxk09/bin/lxnet  /usr/lexinkjet/08zero/bin/

5. Add wireless printer through CUPS through the printer setup.

URI: lxnet://<ip address of the printer>:1/

Hope that helps! Lots of credit to Lexmark's email support they did a great job and I only did a little editing on the phrasing.

---

### Post by YoshiroShin on 2010-10-07
Well it's 32 bit only. Ubuntu still installed it but it won't work and that's probably why.

---

### Post by d4m1r on 2012-11-29
Just wanna update to say I got my lexmark x4690 working perfectly via wifi on Ubuntu 12.04 x64 LTS....It works even better under linux than under Windows!

I didn't have to install any drivers (unlike Windows), but instead I configured it at a network printer and Ubuntu detected and configured it right away :P

Only used the printing aspect though...Don't know if the scanner etc work under Ubuntu...

---

