---
title: "Printer Canon Pixma MG5250"
date: 2010-11-10
forum: Hardware
---

### Post by Frankynov on 2010-11-10
Hello !

I'm planning to buy a new printer, the Canon Pixma MG5250.

[IMG]http://news.idealo.fr/wp-content/uploads/2010/09/canon_pixma_MG5250.jpg[/IMG]

The thing is, I can't find any linux driver on the Canon website and someone in a french forum reported it to no work in Ubuntu :(

Has anybody tried it and had positive results ?

Thanks !

François

---

### Post by peertje888 on 2010-11-24
Smart on asking that question first...we already bought one ](*,)

I have opened a support ticket at canon. 

So frustrating: there is an app for smart phones to print, but on my Ubuntu machine it is impossible!

The printer prints photo beautiful! Only the characters aren't as sharp as the laser printer we had before. This is surprising me as the resolution is way higher! 2400x9600dpi while the laser printer was 600x1200dpi

When I found a driver, I'll post it here ;)

---

### Post by Jacko1 on 2010-11-27
Hi, I found that the Canon websites are not synchronized.
In the Asian pages you find linux drivers for MG5100 and MG5200 series.
[http://support-asia.canon-asia.com/P/search?model=PIXMA+MG5270&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MG5270&menu=download&filter=0&tagname=g_os&g_os=Linux)
I installed one of the deb package for my MG5150 and at least the printer works.
However, I'm having troubles with the scanner, as both the simple scan and the Xsane do not recognize it.

J.

---

### Post by PeterF54321 on 2010-12-31
The Canon European pages now have Linux drivers listed for this printer.

[http://software.canon-europe.com/products/0010889.asp]("http://software.canon-europe.com/products/0010889.asp")

---

### Post by eljopc on 2011-01-02
> **PeterF54321 said:**
> The Canon European pages now have Linux drivers listed for this printer.

[http://software.canon-europe.com/products/0010889.asp]("http://software.canon-europe.com/products/0010889.asp")

This is SO GREAT, but how do I install these drivers on Ubuntu 10.10?

---

### Post by eljopc on 2011-01-02
> **PeterF54321 said:**
> The Canon European pages now have Linux drivers listed for this printer.

[http://software.canon-europe.com/products/0010889.asp]("http://software.canon-europe.com/products/0010889.asp")

This is SO GREAT, but how do I install these drivers on Ubuntu 10.10?

---

### Post by sjosul on 2011-02-05
Assuming you downloaded the file "MG5200series-printer_driver.tar", just extract it. Then extract the "cnijfilter-mg5200series-3.40-1-deb.tar.gz" file. In the terminal, navigate to that folder:

```
cd Downloads
cd MG5200series-printer_driver
cd cnijfilter-mg5200series-3.40-1-deb
```

Then install:

```
sudo ./install.sh
```

Follow the onscreen prompts. I had already connected the printer using wifi (this is done on the printer), and the setup in terminal recognised it immediately. The whole process took about 30 seconds.

---

### Post by sjosul on 2011-02-05
To add the scanner function:

Download the "MG5200series-scanner_driver.tar" software from the canon website [here]("http://software.canon-europe.com/software/0040260.asp?model="). Extract, and in the extracted folder, extract the "scangearmp-mg5200series-1.60-1-deb.tar.gz" file.

Install the software in the terminal by navigating to the folder you last extracted, and type:
```
sudo ./install.sh
```

Once installed, to run the software, in a terminal type:
```
scangearmp
```

Or, setup a new menu item called "Scanner" or "ScanGear" etc, and use the same command.

I found that when I first ran scangearmp, there was no identified scanner. there is a single button that will search for a scanner. Found it within seconds.

---

### Post by davester65 on 2011-02-23
Just bought one of these printers and configured both printer and scanner in under 5 mins with the help of this thread....Thanks Guys

---

### Post by Asklund on 2011-05-01
Thanks for the tips. 
This driver also works in Ubuntu 11.04 :D

---

### Post by Tohris on 2011-05-04
Did you setup via usb or ethernet/Wifi ?

Does the installer actually compiles anything or is it just already binary?

i'd like to have one of those printers work on a non-x86 appliance (a random NAS)...

---

### Post by lcn on 2011-07-07
I bought this printer and installed the latest drivers for the printer and scanner.
So far so good....
When going throgh the options some remarks and questions arise. Maybe I dont understand all about the printdrivers and the options, but apparently I need help:
In printer properties the Settings page is ok. Policies and Access Control I dont use, so skipped. But 'Printer Options':
**Output resolution**: 600 dpi - UNCHANGEABLE (this printer can do much better)
**Color mode**: RGB - UNCHANGEABLE (ie I cannot change to B&W only !!)
Paper size, Media type and Paper Source seem to give the correct choices.
**Amount of Extension**: 2 (Choices are 0,1,2,3. I have NO clue what this does)
Automatic Duplex printing: Correct choices.
Job options page:
Lots of options of which one seemed useful:
**Output mode**: Choices color or monochrome. HOWEVER when selecting monochrome and 'applying', the option is changed back to 'color'. 

Any help understanding above situation and behaviour, and even better a way to solve these issues would be appreciated.

Leo Noordhuizen

---

### Post by addisor on 2011-07-19
I've just bought one of these fine printers but am struggling with the install script, Any pointers?

addisor@Buffalo:~/Downloads/MG5200series-printer_driver/cnijfilter-mg5200series-3.40-1-deb$ sudo ./install.sh
[sudo] password for addisor: 
==================================================

Canon Inkjet Printer Driver Ver.3.40-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg -iG ./packages/cnijfilter-common_3.40-1_i386.deb
(Reading database ... 166402 files and directories currently installed.)
Unpacking cnijfilter-common (from .../cnijfilter-common_3.40-1_i386.deb) ...
dpkg: error processing ./packages/cnijfilter-common_3.40-1_i386.deb (--install):
 trying to overwrite '/usr/bin/cngpij', which is also in package cnijcom 2.90
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ./packages/cnijfilter-common_3.40-1_i386.deb
Command executed = sudo dpkg -P cnijfilter-common
dpkg: warning: there's no installed package matching cnijfilter-common
addisor@Buffalo:~/Downloads/MG5200series-printer_driver/cnijfilter-mg5200series-3.40-1-deb$

---

### Post by oraslaci on 2011-07-19
Dear all!

I was searching for the driver for a long time.
The one provided by canon is crap. Cannot configure or set anything related to printing.
What I found right now is:
[http://www.openprinting.org/driver/gutenprint](http://www.openprinting.org/driver/gutenprint)

gutenprint version  5.2.7 apparently supports the Canon Pixma MG 5100 printer and it's available for 32 and 64 bit architectures in deb package files.

Hooooray!!!


Happy printing!


P.S. Before installing the deb file, I also uninstalled almost anything related to gutenprint and installed lsb as described in the above link.

---

### Post by MyR on 2011-07-20
Can someone who got this printer to work [submit a report]("http://linuxdeal.com/add-printer.php")?

Thanks!!!

---

### Post by s031jd on 2011-07-25
Canon Pixma MG5220 printer/scanner drivers installed correctly on my pc.  Here's how I was able to install the drivers. 



Printer - [http://support-my.canon-asia.com/contents/MY/EN/0100301702.html](http://support-my.canon-asia.com/contents/MY/EN/0100301702.html)
 Scanner - [http://support-my.canon-asia.com/contents/MY/EN/0100303002.html](http://support-my.canon-asia.com/contents/MY/EN/0100303002.html)
 

 1. Download the deb.tar.gz printer driver files to Downloads folder.
 2. Make new printer directory in the usr folder
 2a. $ sudo mkdir /usr/printer
 3. Copy deb.tar.gz printer files to /usr/printer folder
 3a. $ sudo cp ~/Downloads/cnijfilter-mg5200series-3.40-1-deb.tar.gz /usr/printer/
 3b. $ sudo cp ~/Downloads/scangearmp-mg5200series-1.60-1-deb.tar.gz /usr/printer/
 4. Unpack the tar.gz files
 4a. sudo tar -xzf  cnijfilter-mg5200series-3.40-1-deb.tar.gz
 4b. sudo tar -xzf  scangearmp-mg5200series-1.60-1-deb.tar.gz
 

 5. Install the .deb packages with code: dpkg -i <filename.deb>
 5a. cd cnijfilter-mg5200series-3.40-1-deb
 5a1. I am running 64 bit so I ran the amd64.deb packages
 5a2. sudo dpkg -i cnijfilter-common_3.40-1_amd64.deb
 5a3. sudo dpkg -i cnijfilter-mg5200series_3.40-1_amd64.deb
 5a4. **I had to run both drivers to print
 5a5. Go to Application Menu > Printing > and search for MG5200 printer
 

 5b. sudo dpkg -i scangearmp-mg5200series-1.60-1-deb
 5b1. If dpkg does not work then go into the deb file  
 5b2. cd dpkg -i scangearmp-mg5200series-1.60-1-deb
 5b3. sudo sh install.sh
 5b4. scanner driver installed on my pc

---

### Post by oraslaci on 2011-07-26
[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

this link could be also useful if you prefer the canon drivers

---

### Post by marym on 2011-10-29
Printer stopped working wirelessly on desktop so I have uninstalled all the drivers through synaptic.

Then followed the procedure above but get 

"An error occurred. The package management system cannot be identified."

Any ideas please.

Using Ubuntu 10.04 LTS

---

### Post by marleydude on 2011-11-06
Hello,

When I run
root@jed-A780L:/home/jed# scangearmp

I get the following error messages

(scangearmp:1998): Gtk-WARNING **: Loading IM context type 'ibus' failed

(scangearmp:1998): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

I am able to print just not able to use the Scanner.

Any help would be much appreciated.

---

### Post by doubi on 2012-01-14
My Google-fu was weak on this one, thanks for collecting all the answers here :-)

---

### Post by janisgeiger on 2012-02-06
> **s031jd said:**
> 

 1. Download the deb.tar.gz printer driver files to Downloads folder.
 2. Make new printer directory in the usr folder
 2a. $ sudo mkdir /usr/printer
 3. Copy deb.tar.gz printer files to /usr/printer folder
 3a. $ sudo cp ~/Downloads/cnijfilter-mg5200series-3.40-1-deb.tar.gz /usr/printer/
 3b. $ sudo cp ~/Downloads/scangearmp-mg5200series-1.60-1-deb.tar.gz /usr/printer/
 4. Unpack the tar.gz files
 4a. sudo tar -xzf  cnijfilter-mg5200series-3.40-1-deb.tar.gz
 4b. sudo tar -xzf  scangearmp-mg5200series-1.60-1-deb.tar.gz
 
 5. Install the .deb packages with code: dpkg -i <filename.deb>
 5a. cd cnijfilter-mg5200series-3.40-1-deb
 5a1. I am running 64 bit so I ran the amd64.deb packages
 5a2. sudo dpkg -i cnijfilter-common_3.40-1_amd64.deb
 5a3. sudo dpkg -i cnijfilter-mg5200series_3.40-1_amd64.deb
 5a4. **I had to run both drivers to print
 5a5. Go to Application Menu > Printing > and search for MG5200 printer
 
 5b. sudo dpkg -i scangearmp-mg5200series-1.60-1-deb
 5b1. If dpkg does not work then go into the deb file  
 5b2. cd dpkg -i scangearmp-mg5200series-1.60-1-deb
 5b3. sudo sh install.sh
 5b4. scanner driver installed on my pc

Thanks a lot- it worked. (Amazing, even printing in colour!!) ;) As though I don't know why anyone is so crazy about doing everything via Terminal, couldn't you just as well run Nautilus / file browser as root, do the same and just click on the correct "deb" files after extracting. ?

Another thing: How do deb files work, is it possible to delete them after installation? Will the contents be installed somewhere else or will the system still refer to them? (Eg. is their behaviour similiar to zip-/rar-/files?)

> 
[...] followed the procedure above but get 

"An error occurred. The package management system cannot be identified."
Any ideas please.


I got an error in the first place too, though I cant remember if it was the same. Everything worked after I first installed the correct cnijfilter-common-deb file (either amd64 for 64bit or i386 for 32bit system) afterwards the correct cnij-mg[...]series deb file (the second one needs the first one to be installed).

---

### Post by PapaGary on 2012-02-06
Did anyone try [this]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html")?

---

### Post by Lucidium on 2012-02-07
> **PapaGary said:**
> Did anyone try [this]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html")?

Thanks! Works perfectly for finding and connecting to the Pixma MG520

---

### Post by TDK800 on 2012-02-09
Got the printer working and scanning also with scangearmp.

Has anyone gotten scanning to work with simple-scan? Doesn't detect the scanner.

---

### Post by teHIngo on 2012-02-29
Do all settings work for you? Using the genuine driver from Canon from the brilliant PPA mentioned earlier, setting options **grayscale** or **duplex** printing does not do anything! It always prints in color and single sided for some reason. So in fact, I do not have control over the options.

Currently I'm still on 11.04. It seems like 12.04 has Gutenprint 5.2.8pre which has native support for this printer, so if I can't get that stuff working I will upgrade my dad's PC to that version and hope that works better than Canon's driver.

---

### Post by aikishugyo on 2012-03-09
> **teHIngo said:**
> Do all settings work for you? Using the genuine driver from Canon from the brilliant PPA mentioned earlier, setting options **grayscale** or **duplex** printing does not do anything! It always prints in color and single sided for some reason. So in fact, I do not have control over the options.

Currently I'm still on 11.04. It seems like 12.04 has Gutenprint 5.2.8pre which has native support for this printer, so if I can't get that stuff working I will upgrade my dad's PC to that version and hope that works better than Canon's driver.

You can install gutenprint 5.2.8pre1 from source, it will go into /usr/local and not interfere with the system-installed gutenprint in /usr.

Native is a bit too generous :D We have tried to give as much support for different modes and options, an ongoing task, but the maximum resolution is still only the same as the print-head hardware resolution, namely 600dpi: no weaving algorithm is yet applied (likely in 2.9). Also, color tuning is not done for the vast majority of printers and media types and modes, which limits the usefulness for photographs.

However, all modes are supported: so you should be able to print in greyscale, duplex, to CD and so on, and select modes for various media.

---

### Post by Atanas@ on 2012-05-30
> **TDK800 said:**
> Has anyone gotten scanning to work with simple-scan? Doesn't detect the scanner.

Patching libsane source by adding new IDs (taken from the not yet released sane-backends), like:

#define MG5200_PID 0x1749
...
DEVICE ("Canon PIXMA MG5200", "MG5200", MG5200_PID, 2400, 638, 877, PIXMA_CAP_CIS),

and rebuilding/installing the updated package makes (x)sane and also simple-scan work.
Just make sure you add scanner's IP to /etc/sane.d/pixma.conf.

---

### Post by torbengb on 2012-07-25
I've found a way to make the printer work perfectly with color and duplex. :)

It's documented here: [http://askubuntu.com/a/168090/5786](http://askubuntu.com/a/168090/5786)

(Getting the scanner to work is not addressed yet.)

---

