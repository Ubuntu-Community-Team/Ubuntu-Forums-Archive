---
title: "Canon MF3010 Printer with Scanner Driver Installation"
date: 2012-11-28
forum: Hardware
---

### Post by numbcoffee on 2012-11-28
Hello all,

Before we get stuck into the meat of the post, I'd like to introduce you to my problem.

I love Ubuntu especially now, it's gorgeous and wonderful and since Windows 8 is petrifying to say the least I would like to switch back to it.

Why did I leave? My printer. I, like most newbs struggle with drivers and installing hardware and when presented with a tar.gz file, get spooked.

No matter where I Googled or posted, nobody had any information as to how I could install my printer and scanner and it drove me crazy to the point of saying bye to Linux.

I want to come back but only if my printer will work properly. It's a Canon MF3010 lazer printer with a scanner built in and someone on another post said they'd installed the printer and it was working but not the scanner. Upon asking how they did it, there was no reply.

Any ideas as to how to install it would save my life.
Cheers

---

### Post by offgridguy on 2012-11-28
There have been several threads in the forum regarding canon printers,  in the
recent past.  If you haven't already maybe try a thread search under
canon printer, there may be something that helps.  
:)

[www.linuxquestions.org/questions/linux-hardware-18/canon-printer](www.linuxquestions.org/questions/linux-hardware-18/canon-printer)...


Not sure if you have tried here yet.

---

### Post by pdc on 2012-11-30
hi numbcoffee;

sorry to hear you are having issues..........if you are still out there..pleased to see if I can help ........

when I go here

[http://support-sg.canon-asia.com/P/search?model=imageCLASS+MF3010&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-sg.canon-asia.com/P/search?model=imageCLASS+MF3010&menu=download&filter=0&tagname=g_os&g_os=Linux)

you need the [COLOR="SeaGreen"]Canon UFR driver Linux_UFRII_PrinterDriver_V250_uk_EN.tar.gz[/COLOR] from here

[http://support-sg.canon-asia.com/contents/SG/EN/0100270810.html](http://support-sg.canon-asia.com/contents/SG/EN/0100270810.html)

.........as you say, it is packaged as a tar.gz to make it more compact;

these days though in Ubuntu, if you click to download, the system will ask if you want to open with [COLOR="Plum"]**archive manager**[/COLOR] or [COLOR="Plum"]**save**[/COLOR] ........

........by selecting the former ([COLOR="Plum"]open with archive manager[/COLOR]) you get to see the directory opened ......

....if you are still there, tell us if you are using 32bit or 64bit ..

 .....if 32bit ....the package contains debian packages and they should install fine ......if 64bit I can tell you how to convert the 64bit RPM packages to debian packages to install them .......

....how does that sound ........?

(yes, Canon only supply printer drivers but sane seems to provide complete support so the scanner should be fine with xsane .......)

---

### Post by numbcoffee on 2012-12-01
Thank-you all very much for your help so far.

I am using 64bit at the moment

Kindest regards
NC

---

### Post by pdc on 2012-12-01
so with 64bit, one needs to convert the 64bit rpm packages to deb packages;

(were you using 32bit, it would just be a matter of installing the deb packages.........)

so you need to download the ufr driver and if you download to your Downloads directory?

go here

[http://support-asia.canon-asia.com/P/search?model=imageCLASS+MF3010&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=imageCLASS+MF3010&menu=download&filter=0&tagname=g_os&g_os=Linux)

and you should download the UFR II Printer Driver for Linux Version 2.50 which comes in as [COLOR="SeaGreen"]Linux_UFRII_PrinterDriver_V250_uk_EN.tar.gz[/COLOR]

if I just suggest some commands .......

> [COLOR="Red"]cd Downloads[/COLOR]

> [COLOR="Red"]ls[/COLOR]     .........asks for a list of packages in the Downloads directory......

> [COLOR="Red"]tar -zxvf Linux_UFRII_PrinterDriver_V250_uk_EN.tar.gz[/COLOR]

........that should create a DIRECTORY called [COLOR="Blue"]Linux_UFRII_PrinterDriver_V250_uk_EN[/COLOR] ....and you can verify by 

> [COLOR="Red"]ls[/COLOR]   and you should see it ..... next

> [COLOR="Red"]cd Linux_UFRII_PrinterDriver_V250_uk_EN[/COLOR]

then 

> [COLOR="Red"]cd 64-bit_Driver[/COLOR]

then 

> [COLOR="Red"]cd RPM[/COLOR]

then you need alien installed ......check by 

> [COLOR="Red"]man alien[/COLOR] .......if you get some answers, it is installed..if not......as per here

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

> [COLOR="Red"]sudo apt-get install alien[/COLOR]

......then when installed, we install the COMMON package first..

> [COLOR="Red"]sudo alien -i cndrvcups-common-2.50-1.x86_64.rpm[/COLOR]

.....and then the specific package

> [COLOR="Red"]sudo alien -i cndrvcups-ufr2-uk-2.50-1.x86_64.rpm[/COLOR]

.........that should be the printer driver installed .......

..... and you should be all systems go !!

You can check the drivers are installed by 

> [COLOR="Red"]sudo dpkg -l | grep cndrvcups[/COLOR]

let us know how it goes......................

[COLOR="Blue"]**_NB: a later note added 3 days later!!_**[/COLOR] ........post #80 of this thread [http://ubuntuforums.org/showthread.php?t=1427330&highlight=canon&page=8](http://ubuntuforums.org/showthread.php?t=1427330&highlight=canon&page=8) has the key:

[COLOR="SeaGreen"]BEFORE installing the drivers[/COLOR], [COLOR="SeaGreen"]**_issue the command_**[/COLOR]

> **[COLOR="Red"]ln -s /usr/lib /usr/lib64[/COLOR]**

---

### Post by numbcoffee on 2012-12-01
Thanks again sir for your assistance so far.

I got this

> $ sudo dpkg -l | grep cndrvcups
ii  cndrvcups-common                          2.50-2                                    amd64        Canon Printer Driver Common Module for Linux v2.50
ii  cndrvcups-ufr2-uk                         2.50-2                                    amd64        Canon UFR II Printer Driver for Linux v2.50

Then upon printing a test page it refuses to print and says I have a configuration error. 

In the printer state box under properties it says "Idle - File "/usr/lib/cups/filter/pstoufr2cpca" not available: No such file or directory"

Cheers again :)

---

### Post by pdc on 2012-12-01
so well done..........drivers installed ...........

let's see if the symbolic links will fix things....

despite being 64bit, it would seem something in the driver is looking for 

> [COLOR="Blue"]/usr/lib/cups/filter/pstoufr2cpca[/COLOR]

whereas it should be

> [COLOR="Blue"]/usr/lib64/cups/filter/pstoufr2cpca[/COLOR]

so if you copy and paste the commands

> [COLOR="Red"]sudo ln -s /usr/lib /usr/lib64[/COLOR]

and then 

> [COLOR="Red"]sudo ln -s /usr/local/lib /usr/local/lib64[/COLOR]


......so the driver wants to look in lib.....you are saying...no....look in lib64............

......and I suspect a reboot for good measure........any joy?

the above commands come from post #99 here

[http://ubuntuforums.org/showthread.php?t=1427330&highlight=canon&page=10](http://ubuntuforums.org/showthread.php?t=1427330&highlight=canon&page=10)

---

### Post by numbcoffee on 2012-12-02
I did get joy thank-you so much.

I followed your advice and we got a step closer, it still didn't want to print any test pages though. Then I had a gander at that link you shared with me and someone said in it that they had to manually copy over a file, I did that and then copied the libcannon files and voila! A beautiful test page printed out.

Here's what I did:

>  sudo cp /usr/lib64/cups/filter/pstoufr2cpca /usr/lib/cups/filter
 sudo cp /usr/lib64/libcanon* /usr/lib

Thanks so much you saved my life! :)

---

### Post by pdc on 2012-12-02
that's great; you have helped us all ......

.......so you needed pstoufr2cpca copied into ../usr/lib/cups/filter

.AND.........../usr/lib64/libcanon* across to /usr/lib .....good

.....pleased you have got it all going......... enjoy Ubuntu and the printer!

---

### Post by numbcoffee on 2012-12-03
Now if only we could figure out how to get the scanner set up :)

---

### Post by pdc on 2012-12-03
if you go here

[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

and search on Canon you get here

[http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON](http://www.sane-project.org/lists/sane-mfgs-cvs.html#Z-CANON)

one finds entries such as this

> [COLOR="Blue"]imageCLASS MF3110[/COLOR] USB 0x04a9/0x2660 [COLOR="SeaGreen"]Complete[/COLOR]

complete=degree of support

backend=pixma and man page =sane-pixma

......so it should be supported......

what does 

> sane-find-scanner

and 

> sudo sane-find-scanner

and 

> scanimage -L

and 

> sudo scanimage -L

give you?

---

### Post by numbcoffee on 2012-12-03
I really do appreciate all of your help and time, it's really helping me out.

So with regards to the commands, I started with sane-find-scanner and it threw at me that it couldn't find one and that I should try in root mode so logically I progressed to;

> sudo sane-find-scanner
[sudo] password for ---------: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

Then I tried the sudo scanimage -L and got;

> sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


Cheers again :)

---

### Post by fwking on 2012-12-09
I have not tried the scanner utility/driver but I did make a great discovery today regarding the difficulty of finding a Canon driver for their D530 D550 imageclass laser printers.  There are no drivers and the one from asia just won't work.  The Canon imageclass D530 D550 installs easily using the printer driver resident in Ubuntu 12.10 for the MP3010 printer.  The printer performs as it should in both text and graphics.  Hope this helps those who have one of the superb printers but until now were thinking that Win was the only way.......

---

### Post by OldNovice on 2012-12-09
Wonderful! Mine is 32-bit, and this worked straight off.
Many thanks.
So I can print. Now to check this xsane thing...

---

### Post by OldNovice on 2012-12-09
Dear numbcoffee,
Hope you don't mind me hitching a ride on this train of yours!
Your question was exactly the same as my problem,
except this system is 32-bit, so the printer driver went in
very sweetly. Now I'm also stuck with the scanning.

I'm running Ubuntu 12.04 LTS.
sane-find-scanner gives me a little more. I get the same # lines as you
(without using sudo),
except that it finds something:

found USB scanner (vendor=0x0846, product=0x6a00) at libusb:001:004
found USB scanner (vendor=0x04a9, product=0x2759) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

However, scanimage gives the same error message as you.

Plus, I thought find sane-find-scanner was supposed to
give me a device filename, not stuff like
libusb:001:004
What is that, anyway?

I've read some manpages and tried a few things, but I don't know what
I'm doing here.

---

### Post by numbcoffee on 2013-01-07
Ok I'm dying here...

Had to install Ubuntu, followed everything we discussed before and nothing is happening now... It says everything is fine but still nothing prints.

Any ideas? Could anything have changed?

Cheers

---

### Post by pdc on 2013-01-08
so last time around you had a 64bit install and posts #8 and #10 led me to believe it worked then.........my inclination for a new install; would have been it would have been much simpler for a 32bit install; I believe speed of internet access is more important than anything 64bit can offer..

........ for 64bit making the symbolic links before install seems helpful; 

so for 64 bit the steps are:
1) make symbolic links
2) use alien to convert and install rpm packages to deb (*as Canon only supply 64bit rpm packages*......)

for 32bit
1) install the specific debian packages Canon supplies

---

### Post by numbcoffee on 2013-01-08
Cheers PDC. I just got a brand new PC, Windows 8 was quickly removed haha.
 
I will reinstall using the 32 bit flavour, this PC has the capacity for 32 gigs of RAM, switching to 32 bit isn't going to negatively impact anything is it?
 
Cheers again :p

---

### Post by pdc on 2013-01-08
sounds like a great machine; should hum along! with a 32bit install I hope we can get your printer going quickly

---

### Post by ubun2warrior on 2013-06-10
Hi

Has there been any development for scanner bcoz i am facing the same problem, i am able to print bit no scan. One more info i would like to add here, that i was not able to even print from ubuntu 13.04 bit although the installation was perfect and also i was using the official 64bit drivers ver 2.6 available on the canon site and not converted deb files..

Regards

---

### Post by ilias-utcpd on 2013-10-18
Hello everybody !

I am considering to buy the printer+scanner Canon MF3010, but the product's [dedicated web-page]("http://www.canon-europe.com/For_Home/Product_Finder/Multifunctionals/Laser/i-SENSYS_MF3010/") claims "[COLOR=#9A9B9C][FONT=Verdana]Linux support printing only[/FONT][/COLOR]".

Has someone tried to scan with  this device on Ubuntu 13.04, x86_64  ?

Before making any purchase, I would be very glad to get some confirmation that[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1][COLOR=#9a9b9c] [/COLOR][/SIZE][/FONT]Canon MF3010 does scanning properly on Ubuntu....:confused:


Thanks, Miro

---

### Post by kumaran_manickam on 2013-12-19
Hi,

I try to setup Canon ImageCLASS MF3010 printer for Ubuntu 13.04 but still having issue. I followed steps until #9.
 
When click "Print Test Page" button, I see Screenshot_1.jpg (Processing) followed by Screenshot_2.jpg (Idle) but no activity at printer. Where could go wrong? Please help.

Below are the files listed in related directories:

kumaran@Kumaran-PC:~$ ls -l /usr/lib/cups/filter/pstoufr2cpca
-rwxr-xr-x 1 root root 44294 Dis  19 14:41 /usr/lib/cups/filter pstoufr2cpca


kumaran@Kumaran-PC:~$ ls -l /usr/lib64/libcanon*
lrwxrwxrwx 1 root root    21 Dis  19 14:32 /usr/lib64/libcanonc3pl.so -> libcanonc3pl.so.1.0.0
lrwxrwxrwx 1 root root    21 Dis  19 14:32 /usr/lib64/libcanonc3pl.so.1 -> libcanonc3pl.so.1.0.0
-rwxr-xr-x 1 root root 40648 Mei  29  2013 /usr/lib64/libcanonc3pl.so.1.0.0


kumaran@Kumaran-PC:~$ ls -l  /usr/lib/libcanon*
-rwxr-xr-x 1 root root  40648 Dis  19 14:41 /usr/lib/libcanonc3pl.so
-rwxr-xr-x 1 root root  40648 Dis  19 14:41 /usr/lib/libcanonc3pl.so.1
-rwxr-xr-x 1 root root  40648 Dis  19 14:41 /usr/lib/libcanonc3pl.so.1.0.0
lrwxrwxrwx 1 root root     22 Dis  19 14:32 /usr/lib/libcanon_slim.so -> libcanon_slim.so.1.0.0
lrwxrwxrwx 1 root root     22 Dis  19 14:32 /usr/lib/libcanon_slim.so.1 -> libcanon_slim.so.1.0.0
-rwxr-xr-x 1 root root  27856 Mei  29  2013 /usr/lib/libcanon_slim.so.1.0.0
-rwxr-xr-x 1 root root   1019 Mei  29  2013 /usr/lib/libcanonufr2.la
lrwxrwxrwx 1 root root     21 Dis  19 14:33 /usr/lib/libcanonufr2.so -> libcanonufr2.so.1.0.0
lrwxrwxrwx 1 root root     21 Dis  19 14:33 /usr/lib/libcanonufr2.so.1 -> libcanonufr2.so.1.0.0
-rwxr-xr-x 1 root root 180912 Mei  29  2013 /usr/lib/libcanonufr2.so.1.0.0

---

### Post by 9-chris-n on 2014-01-31
[SIZE=2]BUMP.  

Having the same problem as Kumara_manickam.  Any advice?[/SIZE]

---

### Post by pstefco on 2014-09-30
that problem kind of solved itself for me , it worked after rebooting. Also i found instructions to get the scanner going too on this site [http://jonathan.bergknoff.com/journal/scanning-ubuntu-canon-mf3010](http://jonathan.bergknoff.com/journal/scanning-ubuntu-canon-mf3010)

---

### Post by OldNovice on 2014-10-09
Thanks, guys. It's good to have the scanner in action at last!

I'm now using Ubuntu 14.04, and followed the first part of Jonathan Bergknoff's instructions to download and install 
 sane-backend from source:


In a new subdirectory $HOME/MF3010/sane-backends:


$ sudo apt-get install libusb-dev
$ git clone git://git.debian.org/sane/sane-backends.git
$ cd sane-backends/
$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
$ make

The instructions at the end of that piece,
involving moving stuff in the system, are deprecated in the
forum, and anyway can't be used as they stand with Ubuntu 14.04.


Note that libusb is an absolute prerequisite for
any kind of sane functionality.


The make step takes a long time, with many warnings, but
works, as far as I can see.)


Step 2: Second, I uninstalled the version of libsane that came
with Ubuntu14.04.  This automatically removed xsane and
simple-scan as well.  I used the package manager with the GUI,
Ubuntu Software Center.


Third, in directory $HOME/MF3010/sane-backends:


$ sudo make install
  
With that done,
$ scanimage -V
gives:
scanimage (sane-backends) 1.0.25git; backend version 1.0.25


(Note: you have to have a match of versions here. If you get


scanimage (sane-backends) 1.0.25git; backend version 1.0.23


it means that the old libsane was not removed, or has crept back in.
It will creep back in if you try to reinstall simple-scan
with the package manager, and you'll have to go back to step 2.
)


$ scanimage -L
gives
device `pixma:04A92759' is a CANON Canon i-SENSYS MF3010 multi-function peripheral


You are now good to go.
$ scanimage -h
 gives help.


$ sudo scanimage >filename.pnm
gives scary warnings, and I hope I haven't just installed
a trojan, but it
scans whatever is on the scanner plate and saves it as a pnm,
which you can manipulate using gimp (for instance)
into any format you like.:p

---

### Post by stefan_ioan on 2015-02-27
> **OldNovice said:**
> Thanks, guys. It's good to have the scanner in action at last!

I'm now using Ubuntu 14.04, and followed the first part of Jonathan Bergknoff's instructions to download and install 
 sane-backend from source:


In a new subdirectory $HOME/MF3010/sane-backends:


$ sudo apt-get install libusb-dev
$ git clone git://git.debian.org/sane/sane-backends.git
$ cd sane-backends/
$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
$ make

The instructions at the end of that piece,
involving moving stuff in the system, are deprecated in the
forum, and anyway can't be used as they stand with Ubuntu 14.04.


Note that libusb is an absolute prerequisite for
any kind of sane functionality.


The make step takes a long time, with many warnings, but
works, as far as I can see.)


Step 2: Second, I uninstalled the version of libsane that came
with Ubuntu14.04.  This automatically removed xsane and
simple-scan as well.  I used the package manager with the GUI,
Ubuntu Software Center.


Third, in directory $HOME/MF3010/sane-backends:


$ sudo make install
  
With that done,
$ scanimage -V
gives:
scanimage (sane-backends) 1.0.25git; backend version 1.0.25


(Note: you have to have a match of versions here. If you get


scanimage (sane-backends) 1.0.25git; backend version 1.0.23


it means that the old libsane was not removed, or has crept back in.
It will creep back in if you try to reinstall simple-scan
with the package manager, and you'll have to go back to step 2.
)


$ scanimage -L
gives
device `pixma:04A92759' is a CANON Canon i-SENSYS MF3010 multi-function peripheral


You are now good to go.
$ scanimage -h
 gives help.


$ sudo scanimage >filename.pnm
gives scary warnings, and I hope I haven't just installed
a trojan, but it
scans whatever is on the scanner plate and saves it as a pnm,
which you can manipulate using gimp (for instance)
into any format you like.:p


Thanks ... Everything is fine ... scanner works but can use an  application, like simple-scan, xsane? When I tried to install  simple-scan or Xsane (I used the package manager with the GUI, Ubuntu  Software Center), the scanner has not worked ... How can scan multipage  PDF or TIFF multipage? I had to repeat the procedure again;) 
I admit  I'm a beginner ... I do not know how I create group Scanner and how do I  add my scanner (Canon MF3010)... PLS HLP! Thanks!

---

### Post by kurt18947 on 2015-02-28
A possible work-around for those having scanner issues. It might be worth a look at VueScan from Hamrick software. Here is a list of supported Canon machines: [http://www.hamrick.com/vuescan/canon.html](http://www.hamrick.com/vuescan/canon.html).  We have a Canon scanner that is supported by sane ... sorta.  The scanner works, the light in the lid (required for transparencies) does not. VueScan was a simple and not-too-expensive solution for us. You can download the software and try it with your device. If it works, it'll produce an image with a watermark but at least you know it works or doesn't. Purchasing a license removes the watermark.

---

### Post by mattharris4 on 2015-02-28
Would it be possible that an install of Simple Scan would take care of your issues?  I have a Canon MG2120 with a built-in scanner and installing this program from the Ubuntu Software Center allows me to scan with my printer.  It printed by just hooking it up to the computer and telling it to print.  This printer is hooked to a computer running Edubuntu 14.04.

---

### Post by stefan_ioan on 2015-03-01
> **kurt18947 said:**
> A possible work-around for those having scanner issues. It might be worth a look at VueScan from Hamrick software. Here is a list of supported Canon machines: [http://www.hamrick.com/vuescan/canon.html](http://www.hamrick.com/vuescan/canon.html).  We have a Canon scanner that is supported by sane ... sorta.  The scanner works, the light in the lid (required for transparencies) does not. VueScan was a simple and not-too-expensive solution for us. You can download the software and try it with your device. If it works, it'll produce an image with a watermark but at least you know it works or doesn't. Purchasing a license removes the watermark.

VueScan does not recognize my scanner Canon MF3010...
After execution:
Step 2: Second, I uninstalled the version of libsane  that came with Ubuntu14.04 (and Simple Scan is removed). This  automatically removed xsane and simple-scan as well.  I used the package  manager with the GUI, Ubuntu Software Center.
The backend version  for SANE is 1.0.25... If you install Simple Scan this change backend  version for SANE is 1.0.23, and the scanner is not recognized... Any  idea?

---

### Post by pdc on 2015-03-02
VUESCAN

[http://www.hamrick.com/vuescan/canon_mf3010.html](http://www.hamrick.com/vuescan/canon_mf3010.html)

> VueScan does not recognize my scanner Canon MF3010..  ...........thjey would be surprised to hear that; 

I see they advise > On Linux, you need to set up libusb device protections.[http://www.freecolormanagement.com/sane/libusb.html](http://www.freecolormanagement.com/sane/libusb.html)

Before scanning, press the 'SCAN' button on the front panel, choose 'Remote Scanner' and press 'OK'.

Please tell VueScan about the lack of recognition; they ask folks to tell them [http://www.hamrick.com/support/frequently-asked-questions/how-do-i-submit-a-problem-report.html](http://www.hamrick.com/support/frequently-asked-questions/how-do-i-submit-a-problem-report.html)

_____________________

latest version of SANE

Rolf Bensch maintains the sane repository and if you add this ppa [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git) it gives you the latest sane; many would recommend you try this

---

