---
title: "Trusty 14.04 canon gruz PPA"
date: 2014-04-30
forum: Hardware
---

### Post by marksmarks on 2014-04-30
I finally have a Canon printer driver (2400 dpi) working on Ubuntu 14.04 (x32).
(CUPS driver was only 600 dpi)

[B]April 2015 update -->> There is no longer an "unmet dependency on libtiff4".  I checked in Synaptic,  "cnjfilter-ip4500 series", now depends on Libtiff5 >=4.0.3
                                 Please ignore the Libtiff4 details below.[/B]

      * (I did a clean install of a Ubuntu update and so don't even have Libtiff4 on my box anymore.)*    

_Also, Aikishugyo  explains how to print to CD/DVD using the existing CUPS driver._ 

See; [http://ubuntuforums.org/showthread.php?t=2264245&p=13229907#post13229907]("http://ubuntuforums.org/showthread.php?t=2264245&p=13229907#post13229907")

---

### Post by marksmarks on 2014-05-01
The following is one solution I've found ...
(....  Your mileage may vary,  file versions/URLs may change over time, etc.)

* The following worked for my single function printer.   Multi-function/all-in-one devices may require other install steps*.




Add the appropriate gruz PPA (Click on &#8220;*Technical details about this PPA*&#8221; and select your OS version),   then update Synaptic, ...
 

For Ubuntu 10.04, 10.10, 11.04, 11.10;   [https://launchpad.net/~michael-gruz/+archive/canon](https://launchpad.net/~michael-gruz/+archive/canon)

For Ubuntu 12.04, 12.10, 13.04, 13.10, 14.04;   [https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)



B) Then install &#8220;**cnijfilter-common**&#8221;
    Select it in: Synaptic -- Origin, then look for '...PPA michael-gruz-canon...' 


[FONT=courier new]****************************************************************
*** Note: At the following step, us early adopters of Ubuntu 14.04, (Trusty)
*** encountered a unmet dependency on libtiff4 error when installing our
*** printer driver (filter)
***
*** By now, you may not encounter this error.  You can _try installing without_
***  _ manually installing libtiff4 first._
***
*** A) If you too have a unmet dependency on libtiff4, then see manual
***     install instructions below. (Look for more stars *).
***
***
*** For Ubuntu 14.04 Trusty Tahr and Linux Mint 17 Qiana ONLY, you need
*** the libtiff4 library  which is not available via the default repositories, 
*** however, one can download it.
****************************************************************
[/FONT]
C) Followed by the driver (filter) for your printer &#8230;

(Ie:/ for my ip4500 it's &#8220;**cnjfilter-ip4500series**&#8221;.   _You may need to choose a different driver depending on your printer model_.) 
  
 Select it in: Synaptic -- Origin, then look for '...PPA michael-gruz-canon...' 


D) Turn printer on and go to System Settings/Printers/Add

E) Select USB Printer #2 with status readback for Canon IJ
    (Important for utilities cngpijmonlip4500 & cngpij to work)
 

[ATTACH=CONFIG]252702[/ATTACH]


F) Initially installed driver may be CUPS, and limited to 600 DPI 

[ATTACH=CONFIG]252703[/ATTACH]


G) So, select Canon driver instead

[ATTACH=CONFIG]252701[/ATTACH]

[ATTACH=CONFIG]252698[/ATTACH]


H) Notice that in printer properties, one now has 600 &#8211; 2,400 DPI resolution.

[ATTACH=CONFIG]252699[/ATTACH]


I) Before printing, set Color Model to CMYK


Result; I've just printed a Ubuntu 14.04 printer test page on my Canon Pixma ip4500.


****************************************************************
*** **libtiff4 manual install instructions**
***
*** **_Only necessary for Ubuntu 14.04 Trusty Tahr and Linux Mint 17 Qiana!_**
*** Skip the following if you are _not_ using Ubuntu 14.04 Trusty Tahr and Linux Mint 17 Qiana
***
***
*** Ubuntu 14.04 provides libtiff5 but not libtiff4.  (libtiff4 only up to saucy 13.10).
***
***
*** To install the 13.10 (Saucy) version into 14.04, 
***
*** **1) go to the download page**
***
*** [http://packages.ubuntu.com/saucy/i386/libtiff4/download](http://packages.ubuntu.com/saucy/i386/libtiff4/download)
***
*** OR
***
*** [http://packages.ubuntu.com/saucy/amd64/libtiff4/download](http://packages.ubuntu.com/saucy/amd64/libtiff4/download)
***
***
***
*** **And select a mirror to get;**
***
*** libtiff4_3.9.7-2ubuntu1_i386.deb
***
*** OR
***
*** libtiff4_3.9.7-2ubuntu1_amd64.deb
***
***
***
*** **2) Open a Terminal with Ctrl+Alt+t, and in the folder where you downloaded the deb file, type:**
***
*** sudo dpkg -i ./libtiff4_3.9.7-2ubuntu1_i386.deb
***
*** OR
***
*** sudo dpkg -i ./libtiff4_3.9.7-2ubuntu1_amd64.deb
***
***
***
*** **3) Then install the appropriate Canon printer driver/filter as described at step C, above.**
***
****************************************************************


(FWIW: When I installed, a few days after 14.04 was release, I used a .../Main/... source of libtiff4.  From "ftp.us.debian.org".) 


Your mileage may vary, use at your own risk, etc.


**Remaining Question;  - Will adding [B]libtiff4** back conflict with anything? [/B]

----------
Credit for part of this solution due to; 
   "http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mx-series-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/"

"...install Drivers for Canon Printers PIXMA MX Series on Ubuntu 14.04/13.10/13.04/12.10/12.04, Linux Mint 16/15/14/13, Pear OS 8/7 And Elementary OS 0.2"

---

### Post by marksmarks on 2014-05-01
Canon untlity,  cngpij running on Ubuntu 14.04.


[ATTACH=CONFIG]253450[/ATTACH]


Selecting the drivers via Synaptic (easier then command line).

[ATTACH=CONFIG]252798[/ATTACH]

-------------------------
Printer drivers currently in the PPA;

   bjf9000, bjf900, bjs300, bjs500, bjs700, e500, e510, e600, e610, ei250, i255, i550, i560, i850, i860, i950, i990, ip100, ip1800, ip1900, ip2500, ip2600, ip2700, ip3000, ip3300, ip3500, ip3600, ip4000, ip4200, ip4300, ip4500, ip4600, ip4700, ip4800, ip4900, ip5000, ip52000r, ip6600d, ip7500, ip8500, ip90, ix650, mg2100, mg2200, mg3100, mg3200, mg4100, mg4200, mg5100, mg5200, mg5300, mg5400, mg6100, mg6200, mg6300, mg8100, mg8200, mp140, mp160, mp190, mp210, mp230, mp240, mp250, mp270, mp280, mp490, mp495, mp500, mp510, mp520, mp540, mp550, mp560, mp600, mp610, mp620, mp630, mp640, mp750, mp780, mx320, mx330, mx340, mx350, mx360, mx370, mx390, mx410, mx420, mx430, mx450, mx510, mx520, mx710, mx720, mx860, mx870, mx880, mx890, mx920, pixma1000, pixma1500, pixus250i, pixus255i, pixus550i, pixus560i, pixus850i, pixus860i, pixus950i, pixus990i, pixusip3100, pixusip4100, pixusip8600 ; series
-------------------------

---

### Post by pdc on 2014-05-02
great work; many thanks

---

### Post by tmoulder992 on 2014-05-24
Hi,

I'm using mint 17 x64, and was unable to install the driver for my MX340 following these instructions.  filter common installed okay, but trying to install the 340 filter I get:

The following packages have unmet dependencies:
 cnijfilter-mx340series:i386 : Depends: libtiff4:i386 (> 3.9.5-3~) but it is not installable
E: Unable to correct problems, you have held broken packages.

I installed the x64 version of libtiff4.

Thanks,

TM

---

### Post by pdc on 2014-05-24
what do you get if you paste this command into a terminal?

> [COLOR="#FF0000"]dpkg -l | grep libtiff4[/COLOR]

if you get a reply that shows it is installed, can I suggest you run the install commands again for your printer driver? 

Mint has its own forum too; if you wish to post there [http://forums.linuxmint.com/viewforum.php?f=49](http://forums.linuxmint.com/viewforum.php?f=49) (there is a printer section at the top)

---

### Post by tmoulder992 on 2014-05-24
Thanks, but I threw in the towel.  I was using mint 64 bit, and switched to 32 bit.  After that it all went through perfectly.

One side note, the line:

wget ftp.us.debian.org/debian/pool/main/t/tiff3/libtiff4_3.9.7-3_i386.deb

Does not work. The article MarkMarks cited listed it as 

wget ftp.us.debian.org/debian/pool/main/t/tiff3/libtiff4_3.9.7-2_i386.deb

Which worked well.

Thanks!

TM

---

### Post by marksmarks on 2014-05-25
Huh,... those links (in the article) have changed a few times.
 

-- On Ubuntu 12.04 it installed w/o unmet dependences (Libtiff4 3.9.5-2ubuntu1.6 was somehow installed) --

-- However, on my Ubuntu 14.04 box, due to the unmet dependency on Libtiff4 (**three weeks ago**), I have Libtiff4 3.9.7-3 on my system, downloaded from the link I previously cut and pasted from the article into post #2 (above).



When I checked the, Post #2 download links (Ver -3) last night they did not work just as tmoulder992 said.  So I tweaked post #2 links to be Ver. -2.

Without going back and reinstalling I don't want to continue 'tweaking' previously posted links because I could inadvertently introduce errors by not listing exactly, the current steps that worked for me.



1) At the time I installed, the link in the article I cited was;

ftp.us.debian.org/debian/pool/main/t/tiff3/libtiff4_3.9.7-3_i386.deb



2) Later when &#8211; tmoulder992 -- installed, the link in the article I cited apparently was;

ftp.us.debian.org/debian/pool/main/t/tiff3/libtiff4_3.9.7-2_i386.deb




3) Today May 26, 2014, the link in the article I cited is;

cz.archive.ubuntu.com/ubuntu/pool/universe/t/tiff3/libtiff4_3.9.7-2ubuntu1_i386.deb

---

### Post by panvag on 2014-05-30
Thank you, thank you, thank you :D

---

### Post by josvanr on 2014-10-13
The best way to handle this printer is to trash it with a sledge hammer. Or stack pile them and burn.

---

### Post by Peter4444 on 2014-12-10
I successfully installed a Canon MX725 by installing the Canon drivers scangearmp-mx720series-2.10-1-deb and cnijfilter-mx720series-3.90-1-deb. Printer works both on network and USB, but scangear works only in USB. You can activate it by typing "scangearmp" in your terminal and create a launcher in your desktop.

---

### Post by a-you on 2015-02-08
Thanks marksmarks for your guide. It works for me with ubuntu studio trusty 64 bit printing to a canon ip100. All I had to do was to add the ppa for trusty then install “cnijfilter-common” and the “cnjfilter-" pakage for the printer and it prints. In the config dialog it says it prints up to 2400 dpi (though I haven't tested that) so I didn't follow any of the additional steps you outline.

Aslo many thanks to Michael Gruz for providing the wonderful ppa.

---

### Post by vector on 2015-07-31
HI Guys, something broke a few days ago. I no longer can print from Trusty 14.04 64 to Mp640 printer.

This has been working from way back using an old driver and libtiff4 (which is still currently installed)
I have a similar setup on an old 32 bit laptop which still has printer access.
Im assuming something has broken on the 64bit machine.

So in finding this post I went about installing the ppa michael
I tried cnijfilter-common-64 but then that would not let me find a mp640-64 as there is none. It forced me to go back to common-32
and then cnijfilter-mp640series-32.

Adding printer, finds the networked Mp640 and indicates it finds a driver(doesnt say which tho) and prints a test page but viewing the job attributes indicates it is held and the 
job-printer-state-message = cannot specify model number

I have no way of telling if its now using michaels drivers or not
and I dont understand why it cant specify the model number.

I have removed all printers and tried adding them a number of times.
Ubuntu software centre has cnijfilter-common-32 & cnijfilter-mp640series-32 only installed.

I can also ping the printers ip from this pc and print to it from another pc.


Any ideas on what I have missed?

---

### Post by vector on 2015-08-03
OK after hours of fiddling I think Ive fixed it.
I went to dpkg and purged all cnijfilter* from the system
I also purged libtiff4

I then using Michaels ppa and unbuntu software centre
install cnijfilter-common32 and mp640-32
still it wouldnt print.  
"viewing the job attributes indicates it is held and the
job-printer-state-message = cannot specify model number"
So i changed the model number in porperties to the only other one there which was Mp640 version 3.9

bingo we can now print.

---

