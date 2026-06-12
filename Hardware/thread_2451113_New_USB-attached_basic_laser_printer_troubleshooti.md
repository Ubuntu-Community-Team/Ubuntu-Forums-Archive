---
title: "New USB-attached basic laser printer troubleshooting for erratic behaviour"
date: 2020-09-27
forum: Hardware
---

### Post by bdutta on 2020-09-27
Attached a brand-new and fully functional basic laser printer (Brother HL L2321D), that supports USB-only connection to host PC. The host PC is running Ubuntu MATE 20.04. Have installed manufacturer supplied printer driver, and also attempted to use closest generic printer with foomatic drivers (as per manufacturer instructions for getting this printer working on OpenBSD for which no official drivers for this printer are available). The printer was originally attached through a USB2.0 hub, but later connected it directly to the desktop PC, but this change didn't solve the problems, nor did the change of printer type.

The problem I am facing is that documents seem to print, erratically and I cannot quite put my finger on which documents print, when and why, while others don't. For instance, I managed to print 2 pages of a LibreOffice doc without issues, then I managed to print first 2 pages of a 4-page PDF document containing scanned images, but not the last 2 pages. When I retry printing the same PDF again, none of the pages got printed, but CUPS dashboard ([http://localhost:631/](http://localhost:631/)) reports the job as being **completed**. After I restarted the PC and printer, I could again print the first 2 pages but not the last 2 pages of the PDF. Then I could print from Firefox browser. All of these jobs are marked as completed, and I can see all of the corresponding c* and d* files in /var/spool/cups like this:

```
-rw------- 1 root lp    1085 Sep 27 19:24 c00008
-rw------- 1 root lp    1142 Sep 27 19:26 c00009
-rw------- 1 root lp    1113 Sep 27 19:27 c00010
-rw------- 1 root lp    1099 Sep 27 19:37 c00011
-rw------- 1 root lp     975 Sep 27 19:40 c00012
-rw------- 1 root lp    1099 Sep 27 19:48 c00013
-rw------- 1 root lp    1085 Sep 27 19:49 c00014
-rw------- 1 root lp    1075 Sep 27 19:50 c00015
-rw------- 1 root lp    1085 Sep 27 20:00 c00016
-rw-r----- 1 root lp 1001334 Sep 27 19:24 d00008-001
-rw-r----- 1 root lp 1939026 Sep 27 19:26 d00009-001
-rw-r----- 1 root lp 1591467 Sep 27 19:27 d00010-001
-rw-r----- 1 root lp  181213 Sep 27 19:37 d00011-001
-rw-r----- 1 root lp     234 Sep 27 19:40 d00012-001
-rw-r----- 1 root lp  181213 Sep 27 19:48 d00013-001
-rw-r----- 1 root lp 1001334 Sep 27 19:49 d00014-001
-rw-r----- 1 root lp 1001335 Sep 27 19:50 d00015-001
-rw-r----- 1 root lp 1001334 Sep 27 20:00 d00016-001
drwxrwx--T 3 root lp    4096 Sep 27 19:48 tmp

```

Please note that I had already tested this printer earlier in the day with my work laptop running Windows 10 Enterprise, by printing various documents of various types -- Word doc, PDF, Excel, image from Paint etc., ranging from 1 page to 5 pages, all worked fine.

How can I troubleshoot to find what's going on ? Why am I not able to reliably print the entire document each time ? Why are the c* and d* files piling up, and why does CUPS show that the job is completed when it is clearly not. Note that even when files don't get printed, I can hear the print (which is perhaps on standby) wake-up and whirr a bit (similar to when printing actually does happen), but the whirring does down shortly after.

---

### Post by oldfred on 2020-09-27
Too many drivers could be creating conflicts.

I just plugged my Brother in & it worked.

```
fred@Z170N-focal:~$ lpstat -l -e
Brother_HL_L2390DW network none ipp://Brother%20HL-L2390DW._ipp._tcp.local/
HL_L2390DW network none ipp://HL-L2390DW._ipp._tcp.local/


```

And Ubuntu now uses driverless printing.
[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

---

### Post by bdutta on 2020-09-27
Thanks for the answer and a very useful tip. Please note that my printer is a very basic model, it is not a standalone network printer, but a USB-only one. The printer you have can operate as a standalone network printer (just checked the specs which say that this is a wireless capable printer). AFAIK, IPP support on network printers is a given but IPP-over-USB support from what I understand is not so common (my conjecture), perhaps. Found no mention of IPP-over-USB on Brother website or find any discussion on this so far.

However, I am willing to give it a shot. I suppose what this means is that I need to uninstall the Brother manf. driver, and try CUPSDriverlessPrinting to see if it helps. OTOH, isn't there some standardized mechanism to troubleshoot such issues with printers on Ubuntu ? Some logfiles where actual success or failure of a print job is captured ?

---

### Post by oldfred on 2020-09-27
If you boot live installer, after a minute does it show installing printer.
I normally boot live installer from HDD or SSD and it immediately shows adding my printers.

Have had some issues getting scanners to work. It somehow has multiple printers automatically configured. Tried deleting some & it just reinstalls them. And default for printing did not seem to work for scanning but one of the others did?

My Brother is using USB. My wife did print a recipe from her iPad using wireless, but do not remember if I did anything extra to get WiFi to work or not.

---

### Post by SeijiSensei on 2020-09-28
IPP is used to send print files via TCP/IP. It doesn't run over USB. You could use it to send print jobs from other computers to one with the printer connected via USB.

I'd rip out everything you installed, then reconnect the printer and see if Ubuntu recognizes it. I use driverless printing with my Brother.  If it's not recognized immediately, open a browser and go to [http://127.0.0.1:631/](http://127.0.0.1:631/) and use the native CUPS interface to install it.

---

### Post by bdutta on 2020-09-28
Thanks @oldfred, you were spot on and your advice turned out to be quite useful.

First, I live-booted into Ubuntu MATE 20.04, connected the printer, switched it ON, and voila Ubuntu auto-detected it correctly (as being part of the Brother HL L2320D family). Test printout was successful, as were few multipage PDFs (i.e. for the first time, I could print a full PDF of 8-10 pages via Linux).

Next, I booted back onto the disk installed Ubuntu MATE 20.04, where the manf provided driver was installed. Then removed the manf. provided drivers. Repeat the drill i.e. connect the printer, start it - but this time it didn't quite pop up the "found printer" pop-up, but through Control Center, Printers, I could Add printer and it did find the USB connected printer just fine, of right type too, and so far, seems to work fine.

---

### Post by slickymaster on 2020-09-28
*Thread moved to **Hardware**.*

---

### Post by bdutta on 2020-09-28
Thanks @SeijiSensei, reached the same conclusion indeed.
Next stop, figuring out how to set up this host to become the printer server, that can accept jobs over the network from other devices s.a. my WindowsPC and mobile phones.

---

### Post by SeijiSensei on 2020-09-28
[https://ubuntuforums.org/showthread.php?t=2451101](https://ubuntuforums.org/showthread.php?t=2451101)

---

### Post by iamjiwjr on 2020-10-16
Just switch to Solus, LMDE, Deepin, Fedora, openSUSE, or Manjaro. They all install and work with Brother printer scanners easily and work pretty much flawlessly. Ubuntu has had a thing with a bunch of Brother scanner and printer models for many years. It obviously doesn't matter to them to do anything about the problem. Post after post on this and other forums reflects this reality. A bunch of other non-'buntu based distros DO think it matters. And it works. Maybe it's tine to consider a change.

---

