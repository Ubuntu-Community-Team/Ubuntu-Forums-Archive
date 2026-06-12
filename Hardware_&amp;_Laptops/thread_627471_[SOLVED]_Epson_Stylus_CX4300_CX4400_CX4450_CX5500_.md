---
title: "[SOLVED] Epson Stylus CX4300 CX4400 CX4450 CX5500 CX5600 DX4400 DX4450"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by Axx83 on 2007-11-30
_Please anyone who reads this guide help me install the official printer driver with Ubuntu, i've run a lot of difficulties and still did not make it to work!!!_
[http://forum.ubuntu-fr.org/viewtopic.php?pid=1499142](http://forum.ubuntu-fr.org/viewtopic.php?pid=1499142) (this is in french)
[http://forum.ubuntu-it.org/index.php?topic=142737.msg941930](http://forum.ubuntu-it.org/index.php?topic=142737.msg941930) (this is in Italian)(I am Italian but no good with linux tough)
THANKS

**To make the scanner work in Ubuntu 7.10**:

DO NOT install the libsane-extras, they did not work for me, uninstall it if you did it previously before trying this.
NOTE this procedure doesn't work with a 64 bit system, and I don't really know how to make it work...sorry.

Download the drivers from:
[Avasys official Epson drivers]("http://www.avasys.jp/english/linux_e/dl_spc.html")
select your printer and then select Debian, then Others. Select country and then personal use. Download the files listed as scanner drivers for gcc 3.4 (the first 2 .rpm under gcc 3.4)

Open the terminal and insert the following commands.

Install Alien and sane utils
```
sudo apt-get install sane sane-utils xsane alien fakeroot
```

Enter the directory of the downloaded files and Debianize the files:
```
fakeroot alien iscan*.rpm
```

Install the deb created
```
sudo dpkg -i iscan*.deb
```

(_automatic procedure_) Now let's select the driver and comment out scsi then un comment usb:
```
sudo perl -p -i.bak -e 's/epson\n/epkowa\n#epson\n/g' /etc/sane.d/dll.conf
sudo perl -p -i.bak -e 's/scsi EPSON\n/#scsi EPSON\n/g' /etc/sane.d/epkowa.conf
sudo perl -p -i.bak -e 's/#usb\n/usb\n/g' /etc/sane.d/epkowa.conf
```
And you're done modifying the files. (_end automatic procedure_)

*Just to be extra correct I'll insert the manual procedure to modify the files:*
(_manual procedure_) Now let's select the driver and comment out scsi then un comment usb:
```
sudo gedit /etc/sane.d/epkowa.conf
```
put # in front of scsi entry, do it the other way with usb entry, save close.
```
sudo gedit /etc/sane.d/dll.conf
```
comment out the epson entry and insert a new one just below it called epkowa, save close. (_end of manual procedure_)

Let's add the scanner to the system
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```
by adding a new entry
```
# Epson Stylus CX-4300 CX-4400 CX-4450 CX-5500 CX-5600 DX-4400 DX-4450
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="083f", MODE="664", GROUP="scanner"
```

Restart the system

Now run the scanner identifier
```
sane-find-scanner
```
and see where it is located as a usb, the scanner will always have product=0x083f
Modify the permission
```
sudo chmod 0755 /proc/bus/usb/*/*
```
The asterisks can be 001/002 or 001/003 or whatever, that depends on the response above.

Now we can run the program
```
iscan
```

It should work.

If you want to use xsane it should work as well, modify the permission:
```
sudo chmod 0755 /usr/bin/xsane
```
and run it either in a terminal or with the menu.

---

### Post by martinw89 on 2007-12-12
Thanks, I've got my CX4400 working now.  I didn't think anyone else had this thing,  I never can find ink cartridges for the stupid thing.

Just a quick note.  For me, I didn't need to chmod a usb device, in fact, /proc/bus/usb was empty.

Thanks again!

---

### Post by helpdeskdan on 2007-12-16
Another big, big thanks!

Note - you will need sane-utils to do the sane-find-scanner.

A warning - I do NOT recommend this printer to ANYBODY!  After a few test pages (the equivalent to maybe 2 pages of ink at most) the black ink cartridge was empty!  DO NOT BUY THIS PRINTER! If you bought it, DON'T TRY TO GET IT TO WORK IN LINUX! It's not worth the time, go, RUN back to where you bought and return it now!!

---

### Post by martinw89 on 2007-12-18
Yeah, sorry to go off topic, but its like a public service announcement.  This is the absolute worst printer I've ever owned, and I've owned a Lexmark.

> **helpdeskdan said:**
> A warning - I do NOT recommend this printer to ANYBODY!  After a few test pages (the equivalent to maybe 2 pages of ink at most) the black ink cartridge was empty!  DO NOT BUY THIS PRINTER! If you bought it, DON'T TRY TO GET IT TO WORK IN LINUX! It's not worth the time, go, RUN back to where you bought and return it now!!

---

### Post by helpdeskdan on 2007-12-19
My apologies as well for posting off topic, but as you say, it is in a way a public service announcement - DON'T BUY THIS LOUSY PRINTER.  

Oh, and thanks again for posting the how to - maybe I'll still use it as a scanner.

---

### Post by Redone86 on 2007-12-29
I did everything as you said here. I also don't have anything in proc/bus/usb but when I type iscan I see a massage that: Could not send command to scanner. Check the scanner's status. 
Any ideas what I can do about it?
------
I managed to do it myself. Well, actually, it was just my mistake. The scanner is now working so thx a lot!

---

### Post by jonas_e on 2008-01-10
I got the scanner (DX4400) to work now. Thanks! > # chmod 0666 /proc/bus/usb/*/*
did not however work for me. The directory /proc/bus/usb/ is infact empty

However, when I try to print something the printer just shuts down (i.e. power off). Anyone else who has had this problem? Can someone perhaps point me to a solution?

---

### Post by dak-AD on 2008-01-11
thanks, this got my printer/scanner working (first time i got a printer working on linux :) )

to those complaining of the ink running out quickly -- in the install instructions, it says that the very first priming uses a crap-load of ink, and that future cartridges will last longer. anyway, i've managed 13 pages so far with no sign of the ink running out.

---

### Post by ubername on 2008-01-18
> **Redone86 said:**
> I did everything as you said here. I also don't have anything in proc/bus/usb but when I type iscan I see a massage that: Could not send command to scanner. Check the scanner's status. 
Any ideas what I can do about it?
------
I managed to do it myself. Well, actually, it was just my mistake. The scanner is now working so thx a lot!


I'm getting the same message. Can you tell me what your mistake was, 'cos I've probably made it as well but can't figure out how to fix it.

---

### Post by ubername on 2008-01-18
Hi

Does anyone know if the DX4400 needs ink in it to perform as a scanner? I have followed the advice up thread and got to the point where, after a reboot, 'iscan' pops up a window which looks hopeful. When I click preview I get a message which says 'could not communicate with scanner. check scanner status'.

Well I know the 'scanner' is out of ink (after all it's a DX4400 and I have printed a few pages from it.) BTW this was when it was connected to an XP box - it is not a linux issue. This thing either has fumes in its cartridges or extravagantly wastes ink. We got +- 6 pages per cartridge of black ink, so that's about £1 per page. We bought a new HP all-in-one for less money than the DX4400 for my wife's XP box. It hasn't run out of ink, it has an LCD screen to show what your doing, it has a slot for an SD card and can show the pictures on the card and print them without a PC in sight. 

This Epson model is now just R&D  material for me

DON'T BUY ONE

But I would still like to extract some use from it since I'm lumbered with it, so any help gratefully received.

---

### Post by cyberfella on 2008-02-04
well done, well done, well done.  i solved this very problem yesterday for someone with an epson stylus photo rx585 and was about to document my solution for the good of everyone else, but you've already done a sterling job.

Note to anyone using this guide to get an RX585 working, replace the f on the end of idProduct with a c.  and your scanner will finally work! 

i.e. when doing the *sudo gedit /etc/udev/rules.d/45-libsane.rules* part, add these lines instead (subtly different).

# Epson Stylus RX-585
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="083c", MODE="664", GROUP="scanner" 

:)

---

### Post by Axx83 on 2008-02-08
I've fixed the procedure and modified it a bit, what I ask you to do now is HELP me install the Fùç£ìng epson pips driver in ubuntu !!!!!!!!!!!!!!!!!!!!

I know it's tricky but YES WE CAN.

please help me.

---

### Post by micha137 on 2008-02-27
Hi there, 

I have a problem with getting the scanner driver for my newly aquired Epson DX4400 to work with one of my two ubuntu gutsy systems.
Following the procedure as described in this thread worked like a charm with my notebook.
Doing the same with my desktop I keep getting the error message: "Could not send command to scanner..."upon starting iscan.
I suspect the reason might be that the notebook had no scanner or printer installed before and in contrast the desktop may have some ruins of past unsucessful  attempts to get a lexmarkX1190 scanner to work.

I have gone trough the procedure of uninstalling and/or deleting anything I could find that related to scanning (including sane, sane-utils, old lexmark files,  etc...) and installed everthing anew including the epson specific steps over and over again. It is as if I am bouncing into a wall - I am just stuck at getting the same error message again.
 Please can someone give me a hint or a guess about  a conflicting peace of data I might not have thought about yet.

regards
   micha137

---

### Post by Axx83 on 2008-03-05
mmm that's hard, dirty upgrades or driver installation that causes problems is something that happened to me a lot in the past. now I am just as expert as before but I reinstall the system when something like that happens, it's really faster that way.

---

### Post by Axx83 on 2008-03-12
I've edited the guide, now it's PERFECT

---

### Post by oldsoundguy on 2008-03-12
I have NOT attempted to install a multi-purpose Epson an any of my computers as I have a 3 in one HP and a 4 in 1 HP that installed out of the box even with the xsane working perfectly.  

But as a tip with any Epson that uses the small carts and many color carts .. such as the 8 small carts used in the  R1800 (those drivers are in gutenprint) .. those printers are PHOTOGRAPHY printers and really NOT intended for printing a lot of text (using a lot of BLACK ink) .. still and all, the carts are 9 bucks on eBay delivered from Hong Kong .. genuine stuff and vacuum sealed.  Pays to get a couple of extra blacks if you are stuck printing a bunch of text on a photo printer.  AND if you do a LOT of text, and it is all black and white, get a used Laser off of eBay for that .. save a LOT of money and grief!

---

### Post by gavinjb on 2008-04-06
Hi,

I have just followed this thread and got the scanner part of my printer working, but I am having no luck with the Printer I have seen some comments that installing the D68 or DX3850 works, but after installing the Guten printer driver for the D68 I cant see it listed in the printer drivers, do I have to do anything apart from using Alien convert the file to .deb and then run dpkg to install the file.  I am currently using wubi (kubuntu) running 8.04 beta but I cant see where this could cause any problems.

On an additional note I have seen a lot of complaints about ink, if you read the manual you will see that the first cartridge is used very quickly but additional cartridges should be ok (or at least my second cartridge is still going strong after 50-100 A4 sheets printed)


Thanks,


Gavin,

---

### Post by ptero on 2008-05-02
yeah, same thing here. no entries in /proc/bus/usb
```
$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x083f) at libusb:001:003
found USB scanner (vendor=0x2040, product=0x7070) at libusb:002:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
$ sudo chmod 0755 /proc/bus/usb/*/*
chmod: cannot access `/proc/bus/usb/*/*': No such file or directory

```
i can scan already, but only under as root, which isn't that nice...

---

### Post by helpdeskdan on 2008-05-04
Anybody have any luck in Hardy?  /etc/udev/rules.d/45-libsane.rules doesn't exist and proc/bus/usb is empty.  

Oh wait... I just got it.  Go back to the website and get the plugin too.  (Didn't think I needed this)  Do this:

fakeroot alien --scripts iscan-plugin-cx4400-2.0.0-0.c2.i386.rpm
sudo dpkg -i iscan-plugin-cx4400_2.0.0-1_i386.deb 

I never changed any usb permissions, groups, nor libsane rules, but it works fine!  In xsane as well!  Special thanks to Ueullue:

[http://uellue.de/blog/single.php?date=1192278660](http://uellue.de/blog/single.php?date=1192278660)

Hope that helps somebody!

Thkx for comments about cartridge life.  Does it apply to color too?  Maybe I'll just print everything in black and white, as that is the only spare cartridge I have.

---

### Post by helpdeskdan on 2008-05-07
When it's in power saving mode and I try to print, all the lights turn on then the printer turns off.  Anybody else have this problem?

---

### Post by Sawubona on 2008-06-02
Wow, I love you Axx83. I couldn't get this thing to work in windoze vista and thought i would have no chance of getting it to work here. I even emailed epson to get help installing the driver and they pretty much told me no luck. I'm brand new to ubuntu (1 month) and everyday i am convinced more and more i've made the right move. Thanks.

---

### Post by mailbinoy on 2008-06-03
To get the printer working, make sure gutenprint is installed
configure the printer to use cx3800 driver(not the cx5500 driver). and it should work

---

### Post by oldsoundguy on 2008-06-03
No, it does not have to have ink in it to work as a scanner (does as a copier).  But there has to be cartridges in it in order for it to do it's warm up, test thing. (you will get a low ink message).

---

### Post by Trevor Jones on 2008-06-12
Thanks Axx83 that's got my scanner function working on myCX5500.  Did you ever get the thing to print - and if so please tell me how?

---

### Post by balta on 2008-06-25
epson stylus dx4450
simply perfect! great thank you very much

---

### Post by vincentvee on 2008-06-27
> **Trevor Jones said:**
> Thanks Axx83 that's got my scanner function working on myCX5500.  Did you ever get the thing to print - and if so please tell me how?
i am using the cx5500 and i got it to print using a dx4050 driver which is in your printer dialog in ubuntu at system>administration>printing, see screenshot attached in the line where it says printer make and model click change button and scroll down till you find dx4050 and select it, your printer should work then

---

### Post by vincentvee on 2008-06-27
> **Axx83 said:**
> I've fixed the procedure and modified it a bit, what I ask you to do now is HELP me install the Fùç£ìng epson pips driver in ubuntu !!!!!!!!!!!!!!!!!!!!

I know it's tricky but YES WE CAN.

please help me.
use the dx4050 driver you already have and your printer will work

---

### Post by ozp on 2008-07-08
how about update this for 8.04?

with 8.04 the printer cx5600 print out of the box
no scanner out of the box
no ink level out of the box

---

### Post by ianmillington on 2008-07-11
I bought the DX4400 this morning (before I read all the negative posts, alas!

I'm running kubuntu Hardy on a dell laptop. 

However, a breakthrough as there is an Asus EE driver on the Epson website. 1 single install script and hey presto the printer works. Guess they figured it would help them if they could get it to work on the ee. Maybe others will follow suit and we will all benefit.

Ian

PS - no joy with the scanner yet though!

---

### Post by TOOOL on 2008-07-16
any chance of posting a link to the asus eee driver as i am having trouble finding it   have a cx5500   and having no luck getting it to run
cheers

---

### Post by ianmillington on 2008-07-19
They seem to be the same so try here.

Ian


[http://esupport.epson-europe.com/ProductHome.aspx?lng=en-GB&data=lkuCfcvA9cxT7ZOxnRwAsnNbhaCPzDChCc1vy4hYrI0U003D&tc=6](http://esupport.epson-europe.com/ProductHome.aspx?lng=en-GB&data=lkuCfcvA9cxT7ZOxnRwAsnNbhaCPzDChCc1vy4hYrI0U003D&tc=6)

---

