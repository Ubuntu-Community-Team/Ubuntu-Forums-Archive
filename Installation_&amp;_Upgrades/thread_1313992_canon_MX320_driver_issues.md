---
title: "canon MX320 driver issues"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Sgt.Schultz on 2009-11-04
I've recently installed Ubuntu 9.10 64-bit, and am having trouble getting the canon MX320 drivers working. The drivers I have downloaded for the printer were stored in a tar.gz file, inside there were two .deb files, however they are for a 32-bit system and won't install. Therefore I'm wondering if anyone has a 64-bit version or an alternative way to get my printer working. Any help would be greatly appreciated.

:edit:
I have recently fixed the problem I was having with the driver installation. For those of you who are in the same boat as I was in use the "sudo dpkg -i --force-architecture (file name)" command to force installation of the 32 bit drivers.
:edit:

---

### Post by fawasp on 2009-11-11
I just install mx320 driver and it's now working well, 
there are both scanner and printer drivers can be download at canon Thailand, please visit this link and choose the driver for Debian!

[http://support-th.canon-asia.com/P/search?model=PIXMA+MX328&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-th.canon-asia.com/P/search?model=PIXMA+MX328&menu=download&filter=0&tagname=ca_os&ca_os=Linux)

inside this link there are 6 links for you to choose, you can choose the 3rd link "MX320 series ScanGear MP Ver. 1.30" for the scanner driver
and you can choose the 6th link "MX320series IJ Printer Driver Ver. 3.10" for the printer driver 

to Install
1.Extract the file .tar.gz
2.Double click on install.sh 
3.Click Run in Terminal
4.Go to System>Administration>Printing
5.Click New (at the top left)
6.The Canon MX320 will be there ready to be chosen
7.Follow the process of adding new printer
:)


Ps. I'm now using it on UBuntu 9.10

---

### Post by neversleep54 on 2010-01-27
> **fawasp said:**
> I just install mx320 driver and it's now working well, 
there are both scanner and printer drivers can be download at canon Thailand, please visit this link and choose the driver for Debian!

[http://support-th.canon-asia.com/P/search?model=PIXMA+MX328&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-th.canon-asia.com/P/search?model=PIXMA+MX328&menu=download&filter=0&tagname=ca_os&ca_os=Linux)

inside this link there are 6 links for you to choose, you can choose the 3rd link "MX320 series ScanGear MP Ver. 1.30" for the scanner driver
and you can choose the 6th link "MX320series IJ Printer Driver Ver. 3.10" for the printer driver 

to Install
1.Extract the file .tar.gz
2.Double click on install.sh 
3.Click Run in Terminal
4.Go to System>Administration>Printing
5.Click New (at the top left)
6.The Canon MX320 will be there ready to be chosen
7.Follow the process of adding new printer
:)


Ps. I'm now using it on UBuntu 9.10

don't work on my ubuntu 64 !!!!!!!!!!

---

### Post by manu7irl on 2010-05-14
That did the trick for me on Ubuntu 10.04 64 bit!
Simply run in terminal from the folder where you placed the 2 packages :

Code:

```
sudo dpkg -i --force-architecture ./cnijfilter-common_3.10-1_i386.deb

```
and then :

Code:

```
sudo dpkg -i --force-architecture ./cnijfilter-mx320series_3.10-1_i386.deb

```




Emmanuel.

Pc configuration :
motherboard : gigabyte GA-MA785G-UD3H
processor : AMD Athlon II quad core 630 2.80Ghz
memory : 2 x 2 Gb DDR2 800Mhz
video card : onboard ATI HD4200
OS : dualboot grub2 Ubuntu 10.04 64bits / Windows 7 32 bits

---

### Post by Jason Argonaut on 2010-05-16
> **neversleep54 said:**
> don't work on my ubuntu 64 !!!!!!!!!!
  


The Canon drivers don't install on my amd64 lucid lynx either.

Default gdebi + gtk-gdebi do *not* have  (--force-architecture) as an option, as manu7irl says.  Perhaps there's a newer version.

It's possible to open the .gz's  with ark &  copy individual .so, .ini, and .ppd files to prescribed locations. 

Foomatic-configure accepts the PPD file (canonmx320.ppd).  Desktop applications can "see" the printer.   

dmesg shows the hardware being detected at USB plug-in-time.

xsane cannot detect a scanning device (meaning --> no drivers).

---

### Post by francois138 on 2010-05-28
For people running ubuntu amd64, 

[http://ubuntuforums.org/showthread.php?p=9374632#post9374632]("http://ubuntuforums.org/showthread.php?p=9374632#post9374632")

This worked for me, click the link above for more details.

---

### Post by gengbinich on 2010-07-05
I went to:
[http://ubuntuforums.org/showthread.p...32#post9374632]("http://ubuntuforums.org/showthread.php?p=9374632#post9374632")

I just tried in my Ubuntu 10.04 amd64 with USB conection and  it works for my MX320!  But it was easier.
Just follow the command line instructions given in the first post with the USB cable disconnected.  Then, instead of going to the "printers configuration", just connect the USB cable and it should configure automatically :KS:KS

---

### Post by pitanu on 2011-01-27
ubuntu is the greatest, the community is the greatest. thanks guys, my mx328 now works on 10.04 after a frustrating day.

---

### Post by andyb132 on 2011-03-15
FAIL This does not work on the latest version of Ubuntu 64 bit.

---

### Post by adrian.h on 2011-03-23
Getting it to install is one thing, but to get it to actually print something is entirely different.  So I installed the drivers, plugged in the printer, and voila it self installs, but when I try and print anything even the test page, it just sits there.  *sigh*  Any ideas?

---

### Post by adrian.h on 2011-03-23
Ok, so looking in to this further, I tried to print a simple pic.  This is what ps faux gave me:

[HTML]USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root      2270  0.0  0.0  75808  1932 ?        Ss   Mar21   0:02 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
lp       20848  0.0  0.1   7096  3336 ?        S    22:41   0:00  \_ MX320-series-FAX 93 adrian pic.gif 1 MediaType=plain InputSlot=asf number-up=1 PageSize=Letter CNExtension=2 job-uuid=urn:uuid:89581596-2ff8-3cca-5df0-08c504ecff18 job-originating-host-name=localhost
lp       20906  0.0  0.0   4012   552 ?        S    22:41   0:00  |   \_ /bin/sh -c /usr/bin/gs -r600 -g5100x6600 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -| /usr/bin/cifmx320 --imageres 600 --papersize letter --media plain --paperload asf --bbox 18,14,595,784 --fit  
lp       20907  5.1  1.1 146864 34572 ?        S    22:41   0:07  |       \_ /usr/bin/gs -r600 -g5100x6600 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -
lp       20908  0.0  0.0   4904  2812 ?        S    22:41   0:00  |       \_ /usr/bin/cifmx320 --imageres 600 --papersize letter --media plain --paperload asf --bbox 18,14,595,784 --fit
root     20849  0.0  0.0  48376  1540 ?        S    22:41   0:00  \_ usb://Canon/MX320%20series%20FAX 93 adrian pic.gif 1 MediaType=plain InputSlot=asf number-up=1 PageSize=Letter CNExtension=2 job-uuid=urn:uuid:89581596-2ff8-3cca-5df0-08c504ecff18 job-originating-host-name=localhost
 [/HTML]

Hmmmm, well that looks like crap.  Here is an image of the tree: 
[IMG]http://i1102.photobucket.com/albums/g453/adrian_h/tmp-l.png[/IMG][IMG]http://i1102.photobucket.com/albums/g453/adrian_h/tmp-r.png[/IMG]

Hmmmm, not sure if that's much better.  Anyway... when I tried this at another time, cifmx320 cpu was at 100 and I had to kill it.  This time, it is doing very little.  Both times the print queue says processing.  Not sure what crap data is being fed to gs or if it just doesn't understand the data coming out of gs.

Suggestions?

---

### Post by pitanu on 2012-09-15
> **fawasp said:**
> I just install mx320 driver and it's now working well, 
there are both scanner and printer drivers can be download at canon Thailand, please visit this link and choose the driver for Debian!

[http://support-th.canon-asia.com/P/search?model=PIXMA+MX328&menu=download&filter=0&tagname=ca_os&ca_os=Linux](http://support-th.canon-asia.com/P/search?model=PIXMA+MX328&menu=download&filter=0&tagname=ca_os&ca_os=Linux)

inside this link there are 6 links for you to choose, you can choose the 3rd link "MX320 series ScanGear MP Ver. 1.30" for the scanner driver
and you can choose the 6th link "MX320series IJ Printer Driver Ver. 3.10" for the printer driver 

to Install
1.Extract the file .tar.gz
2.Double click on install.sh 
3.Click Run in Terminal
4.Go to System>Administration>Printing
5.Click New (at the top left)
6.The Canon MX320 will be there ready to be chosen
7.Follow the process of adding new printer
:)


Ps. I'm now using it on UBuntu 9.10

What would we do without the Ubuntu community?  You guys are the best.  Thanks this worked fine for me, after a couple of tries, but that's my fault as I have a bad habit of skip reading, if you read the whole text it'll work just fine, trust me.

Best regards from Bangkok.

---

