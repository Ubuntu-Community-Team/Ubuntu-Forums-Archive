---
title: "Netgear WG511 v2 Issues"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by himuraken on 2005-10-15
Hi, I have a Gateway Solo model 400SD4 laptop which I just got Breezy 5.10 installed on. So far everthing is working great right "out of the box" except for my Netgear WG511 v2 wireless PC Card. Reading through the forums I noticed a user or two state that it works right out of the install. Neither of the cards two LED's will light up, nor does it show in device manager. Any suggestions on which direction to take this? TIA

---

### Post by ychen on 2005-10-15
You can try [ndiswrapper 1.4]("http://ndiswrapper.sf.net"). I can make it work on Ubuntu 5.04/5.10, but it still has some problems, such as sometime the system freezes.

---

### Post by GeeJay on 2005-10-31
I installed the latest version of Ubuntu (October 2005, default desktop install on Dell Inspiron laptop with PCMCIA wireless card) to find to my joy that the green LED on my Netgear WG511 v2 lit up straight away when I rebooted and enabled it after the install. I then used the GNOME networking tool to set up a 64-bit WEP encryption password and it works fine. 

I used the config pages of my Netgear wireless router to generate a hexadecimal 10-character encryption key and typed it in, set the pull down menu in tool to Hexadecimal (obviously). Make sure in the networking tool that you have enabled the wireless card as the install seems to disable it by default. 

I am impressed with Ubuntu wireless access after the nightmare I had with Mandriva free version of Linux (which nowadays effectively seems to be crippleware).

If you are having problems run iwconfig from the command console, this should show your wireless card usually as eth1 if you have a NIC socket and presumably eth0 if you do not.

I am a newie to Linux like you so good luck.

---

### Post by objectmaster on 2007-08-10
Hmmm, Netgear WG511 v2 does not work the latest version of the Ubuntu desktop version (7.04 - Feisty Fawn), at least not without tweaking your system. 

Hence, if you think you can get this wireless network card (Netgear WG511 v2 Made in : China) with a new installation of Ubuntu, you will be very disappointed. 

I'll try Ndiswrapper and see if I have more luck with some tweak. I'll post any news once I get it to work.

UPDATE: 
Yeah, quite simple to get it up and running: 

(make sure to have your installation CD for the Netgear WG511 v2 in your cdrom drive - assuming you have it mounted on /media/cdrom)

$sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 
$sudo ndiswrapper -i /media/cdrom/Driver/Windows\ 98/WG511v2.inf

You can reboot or re-insert the wireless card...but I bet a Linux guru has a slicker way of doing it.

UPDATE2: Managed to get the internal wireless card of the notebook to work, so I returned the card to get a refund. One more thing though, I had some issues with WAP encryption (which I didn't with the wireless card I got to work later).

---

### Post by irusun on 2007-08-18
What if you no longer have the original CD?  

The driver downloads on the netgear website are exe installer files.  I even tried "installing" the driver on a Windows desktop machine to see if I could extract the files, but that doesn't seem to be working.  Any ideas (aside from trying to get netgear to send me another CD)?

---

### Post by jpneely on 2007-09-15
> **objectmaster said:**
> 
UPDATE: 
Yeah, quite simple to get it up and running: 

(make sure to have your installation CD for the Netgear WG511 v2 in your cdrom drive - assuming you have it mounted on /media/cdrom)

$sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 
$sudo ndiswrapper -i /media/cdrom/Driver/Windows\ 98/WG511v2.inf


UPDATE2: Managed to get the internal wireless card of the notebook to work, so I returned the card to get a refund. One more thing though, I had some issues with WAP encryption (which I didn't with the wireless card I got to work later).

This worked for me.  I have had a difficult time setting up Wireless but this was a piece of cake.  I'm using the WG511v2 and IBM T30 Notebook.

---

### Post by Kappity on 2007-10-10
I have a feeling some preliminary steps are being left out, possibly taken for granted, here. ;)

I just installed Feisty Fawn on an old laptop.  This is the first time I've used Ubuntu.  I installed it with the WG511 v2 plugged in, just in case it would somehow "autodetect" it during setup.  No such luck.

I ran the commands given below, and it apparently installed the Windows 98 driver.  However, there are still no lights on the wireless card, and when I go to network settings, under system, there is nothing there about wireless configuration.

Now I know that I'm simply going to have to do lots of reading if I want wireless connectivity with this computer, no way around it.  But there is a baffling amount of information out there on this subject.  Does anyone have a suggested link for the best "dummies" guide to configuring a wireless card on a linux system?  One that doesn't take it for granted that I already know what these typed commands actually *mean*? :(

> **objectmaster said:**
> Hmmm, Netgear WG511 v2 does not work the latest version of the Ubuntu desktop version (7.04 - Feisty Fawn), at least not without tweaking your system. 

Hence, if you think you can get this wireless network card (Netgear WG511 v2 Made in : China) with a new installation of Ubuntu, you will be very disappointed. 

I'll try Ndiswrapper and see if I have more luck with some tweak. I'll post any news once I get it to work.

UPDATE: 
Yeah, quite simple to get it up and running: 

(make sure to have your installation CD for the Netgear WG511 v2 in your cdrom drive - assuming you have it mounted on /media/cdrom)

$sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 
$sudo ndiswrapper -i /media/cdrom/Driver/Windows\ 98/WG511v2.inf

You can reboot or re-insert the wireless card...but I bet a Linux guru has a slicker way of doing it.

UPDATE2: Managed to get the internal wireless card of the notebook to work, so I returned the card to get a refund. One more thing though, I had some issues with WAP encryption (which I didn't with the wireless card I got to work later).

---

### Post by John Jason Jordan on 2007-12-22
> **Kappity said:**
> I have a feeling some preliminary steps are being left out, possibly taken for granted, here. ;)

I just installed Feisty Fawn on an old laptop.  This is the first time I've used Ubuntu.  I installed it with the WG511 v2 plugged in, just in case it would somehow "autodetect" it during setup.  No such luck.

I ran the commands given below, and it apparently installed the Windows 98 driver.  However, there are still no lights on the wireless card, and when I go to network settings, under system, there is nothing there about wireless configuration.

Now I know that I'm simply going to have to do lots of reading if I want wireless connectivity with this computer, no way around it.  But there is a baffling amount of information out there on this subject.  Does anyone have a suggested link for the best "dummies" guide to configuring a wireless card on a linux system?  One that doesn't take it for granted that I already know what these typed commands actually *mean*? :(

I finally got my Netgear WG511 v2 with Marvel chipset working on Gutsy x86_64 using ndiswrapper. I posted details (including for 32-bit Gutsy) here:

[http://ubuntuforums.org/showthread.php?p=3999047#post3999047](http://ubuntuforums.org/showthread.php?p=3999047#post3999047)

My problem was getting the right driver. The above discussion has a link to 64-bit Windows drivers, not from Marvel or Netgear.

---

