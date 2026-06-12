---
title: "Epson WF-2510 printer"
date: 2014-10-08
forum: Hardware
---

### Post by catgate2 on 2014-10-08
I am back again with Printer Problems and would appreciate a little guidance, please.  
 

 I decided to switch operations from a desktop box with a few years on its back (box A)  to an older box (box B) that has had a recent face lift (new CPU, RAM and a fairly new 500GB HD I had lying about).  
 I cleaned and formatted the 500GB HD with a Gparted CD and then put on Ubuntu 12.04 from a 12  month old download CD (running the live update option).  
 I then copied the files I wanted to keep from the old box on to an external HDD and transferred them to the new box.      So far, so good. All seemed peace and joy.
 

 Then I hit printer troubles. To describe them would be difficult, because of the inconsistency of it all.  When trying to print text it would simply print half a dozen lines of  mixed capital letters and symbols and then eject the paper. If it was a picture it would print a few lines and then abandon it.
 But more often it would do nothing (very quietly).

Oh! one other quaint thing.
When I open Rhythmbox it immediatly starts loading everything that it can find that has the approriate file type to be played (wav.mp3, midi etc) and starts playing.

 The CPUs are :-
 

 Box A      &#8220;Celeron(R) CPU G55 @ 2.6  GHz x 2 32bit&#8221;
 

 Box B      &#8220;Pentium(R) Dual-Core CPU E5700 @ 3.00 GHz × 2&#8221;  
 

 The printer is an Epson WF-2510, new 24 May this year and has worked without trouble up to now.
 

 I have loaded the  same drivers into Box B as were in Box A .

---

### Post by mörgæs on 2014-10-09
Hi, welcome to the fora.

With new hardware you should use the newest of software. How does the printer work in a fresh install of 14.04.1?

---

### Post by pdc on 2014-10-09
Hi catgate;

I wondered what drivers you were using? If you paste this command > [COLOR="#FF0000"]dpkg -l | grep epson-inkjet-printer[/COLOR] into a terminal, and paste back please; it should tell us what you have installed;

________________________

If I were starting from scratch, I would go here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18783&DSCCHK=4ef4d5c29c91ff6c711c196da42d431d2515a5ff) 

I am not clear if you are running 32bit; if you were I would install the [COLOR="#008000"]epson-inkjet-printer-201211w_1.0.0-1lsb3.2_i386.deb[/COLOR]

__________________

for the scanner, I would go here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=31834&DSCCHK=97a5d952171b35e53aa59f7bf93a62e895005382](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=31834&DSCCHK=97a5d952171b35e53aa59f7bf93a62e895005382)

and download and install:

1) DATA PACKAGE [COLOR="#008000"]iscan-data_1.30.0-1_all.deb[/COLOR] (Third from the bottom of the list!!)

2) [COLOR="#008000"]iscan_2.30.0-1~usb0.1.ltdl7_i386.deb[/COLOR] (32bit package if a 32bit system.............and ltd7 as that is for modern systems...............)

3) NETWORK PLUG-IN PACKAGE [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=24993&DSCCHK=fd5cb71b1b7dcca4b2eba38afa9631e914a5e10f](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=24993&DSCCHK=fd5cb71b1b7dcca4b2eba38afa9631e914a5e10f) [COLOR="#008000"]iscan-network-nt_1.1.1-1_i386.deb[/COLOR]	

__________________________

We are running 12.04 as it is a long-term release; (I understand it is supported until 2017) [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) and I would feel it will run well till then; the distro Linux Mint will be releasing its forthcoming releases based on the 14.04 ubuntu, that they plan to use for several years I understood

---

