---
title: "[SOLVED] To install a Samsung CLX-2160 printer on 7.10"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by loza on 2008-01-28
Hello

I bought the Samsung CLX-2160 all-in-one laser printer. The Samsung site and brochures state that it comes with Linux drivers. However, these do not appear to install on Ubuntu 7.10. 

I have tried editing the install scripts to make it 'fit' my system but alas I could not successfully send a print job to the printer.

The good news is that there is a way to get the printer to work with 7.10, and that is to follow the instructions exactly on the [SIZE="2"][foo2qpdl:   	a linux printer driver for QPDL protocol]("http://foo2qpdl.rkkda.com/")[/SIZE]  page of [http://foo2qpdl.rkkda.com/]("http://foo2qpdl.rkkda.com/").

The site took some finding so that is why I'm just highlighting it here in this forum.

However this only applies to the printer and does not contain a driver to support the scanner. On the print out front, the colour management may need some tweaking as some of the colours print very strong.

loza

---

### Post by wormie_dk on 2008-03-14
Have you tried the instructions here:
[http://www.samsung.com/nl/support/productsupport/download/FileView.aspx?cttfileid=1395565&type=Printers&typecode=&subtype=colorlaser&subtypecode=&cmssubtypecode=&model=CLX-2160/SEE&filetype=DR&language=&LSSI=/nl/module/ssi/left/lmenu_printers_colorlaser.sec&RSSI=/nl/module/ssi/right/rmenu_printers.sec](http://www.samsung.com/nl/support/productsupport/download/FileView.aspx?cttfileid=1395565&type=Printers&typecode=&subtype=colorlaser&subtypecode=&cmssubtypecode=&model=CLX-2160/SEE&filetype=DR&language=&LSSI=/nl/module/ssi/left/lmenu_printers_colorlaser.sec&RSSI=/nl/module/ssi/right/rmenu_printers.sec)

Mainly:
[Ubuntu OS Installation]
1. Download and extract the driver
2. Open ''Root Terminal''
3. Execute installation program.
$ sudo cdroot/autorun
4. After intall, PPD path is set again.
$ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung
5. Execute Configurator, and Add your printer model name by Add Printer

---

### Post by bittner on 2008-05-02
I have successfully installed the Samsung CLX-2160 color laser printer and scanner driver with the setup CD that was packed with the printer. (It's a Kubuntu 7.10 system.) I had to start the setup using 'kdesu' otherwise it wouldn't run, and there were some environment variables I had to set manually.

Printing and scanning worked right away, the printer test page is printed out perfectly, but unfortunately all color printouts (apart from the CUPS' test page) are kind of blurry, having a kind of violet shade around each text character when printing text (from KDE applications as well as, for example, from Firefox). Switching the default to black&white results in perfect b&w printouts, though. The next problem here is, however, that on the user level switching between b&w and color does not work: You have to do this as root (or more precisely, as a CUPS administrator). This is probably a permission problem, but I'm not sure.

The shipped applications (Samsung Smart Panel) are nice, but still not 100% elaborated from a usability point of view. (E.g. the scanning application is not easily reachable, and it's not able to launch it as a separate standalone application (must go through "Scanner", "Properties" or so), and KDE's kooka scanning application (which I personally don't like) crashes, I believe because of a driver issue.

Unfortunately Samsung does not seem to have a forum for Samsung device owners, and searching the web I was unable to find hints on how to manage the problems mentioned above. I can't believe I am the only one have printing problems on Linux. Does anyone know of resources for discussion on Samsung printers? Or do I need to send an e-mail directly to Samsung support?

---

### Post by wormie_dk on 2008-05-03
> **bittner said:**
> 
Printing and scanning worked right away, the printer test page is printed out perfectly, but unfortunately all color printouts (apart from the CUPS' test page) are kind of blurry, having a kind of violet shade around each text character when printing text (from KDE applications as well as, for example, from Firefox). Switching the default to black&white results in perfect b&w printouts, though.
The samsung linux driver is very bad... Try this one instead: [http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

I am using it at the moment and get same quality prints in Windows and Linux now!

About switching between bw/color I simply added two printers. One for bw and one for color, however I dont have to supply passwords in gnome if changing printer settings

---

### Post by j4ni on 2008-05-09
> **wormie_dk said:**
> The samsung linux driver is very bad... Try this one instead: [http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

I am using it at the moment and get same quality prints in Windows and Linux now!

About switching between bw/color I simply added two printers. One for bw and one for color, however I dont have to supply passwords in gnome if changing printer settings

Does your CLX-2160's scanner work with foo2zjs?


-j4ni

---

### Post by wormie_dk on 2008-05-09
No I use the Samsung driver for scanning

---

### Post by loza on 2008-06-23
Hi I'm having real problems which seem to have come about since I have upgraded to Hardy.

Xsane is now saying it cannot find a scanner, although it works on a windows pc fine. I have done a 
> sudo sane-find-scanner -q
 and it gives me 

> found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x3425 [CLX-216x Series]) at libusb:003:002


I tried installing a fresh samsung driver but no change. When I look in the configurator there is no scanner detected...

The printer is still working fine though...

Also I did a > sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages). 

any ideas please? :confused:

loza

---

### Post by spandon on 2008-06-29
Hi 1oza,
I to have just aquired a CLX-2160 Printer and had the same problem as yourself.
The automatically installed printer driver for this printer in Ubuntu (i am using Ubuntu 8.04)works perfectly as a printer, but the Scanner did not work for me also.
I searched the threads on here and also contacted Samsung, and between them I came to the conclusion that what was needed was to download the Samsung driver and install it that way.
This I did, and once I installed it, there was a Samsung Unified Printer Configurator icon on the Desktop also an entry in the Applications Menu for this printer.
I also found out that the driver needs to be re-directed to be able to use the USB please see the item here, which I also did (delete the # from 4 lines) [http://ubuntuforums.org/showpost.php...&postcount=114](http://ubuntuforums.org/showpost.php...&postcount=114) .
After doing this I tested out the Configurator, and still the Scanner was not recognised, then I re-read the Samsung instructions, PRESS the "scan to" button on the printer panel THEN select scan and the scanner worked perfectly.
Hope this helps you?
don

---

