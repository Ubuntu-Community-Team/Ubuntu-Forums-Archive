---
title: "USB to Thermal receipt printer TYSSO PRP-085IIIT keep getting errors"
date: 2015-02-07
forum: Hardware
---

### Post by Zhao_Daniele on 2015-02-07
Hello world
I'm trying to switch from windows 8.1 to LinuxMint 17.1 rebecca
In the process of installing my Thermal receipt printer in this new enviroment, I found it rather dificult, I looked at other similar printers wikis but no one could be as hard as this one because of the low demand.
This printer is ideal for POS stations.
So finaly I found something relevant in a russian website:

[http://www.kaa.org.ua/programmi/drayver-dlya-printera-tysso-prp-085iiit.html](http://www.kaa.org.ua/programmi/drayver-dlya-printera-tysso-prp-085iiit.html)

I started as he say from source:
1 Click download at the bottom of the screen, then agree their therms, then get your file downloaded in Downloads folder
2 extract the file with command line in Terminal: [I]tar -xvf prp085iiit-1.0.0.tar.bz2
3 get inside the created folder with command line: cd prp085iiit-1.0.0
4 command line: [I]cmake -DCMAKE_BUILD_TYPE=Release .
   if you get an error is because you miss some packages, surfing a bit I found the reason, if I still remember, download and install c++, and get back to step 3
5 command line: make
then this error
> ~/Downloads/prp085iiit-1.0.0 $ make
[100%] Building C object CMakeFiles/rasterto_prp085iiit.dir/source/rasterto_prp085iiit.c.o
/home/username/Downloads/prp085iiit-1.0.0/source/rasterto_prp085iiit.c:15:23: fatal error: cups/cups.h: No such file or directory
 #include <cups/cups.h>
                       ^
compilation terminated.
make[2]: *** [CMakeFiles/rasterto_prp085iiit.dir/source/rasterto_prp085iiit.c.o] Error 1
make[1]: *** [CMakeFiles/rasterto_prp085iiit.dir/all] Error 2
make: *** [all] Error 2

[/I]
I'm stuck there could you help me?

Then I tryed the second option for ubuntu, kinda hard to figure out because I installed Mint 17.1 MATE 64, and in their wiki it says compatible with most of hardwares.
1 Click on Menu system section select Software Manager, put your password, then head to where you place your repositoryes and add source:
*deb [http://www.kaa.org.ua/ubuntu](http://www.kaa.org.ua/ubuntu) binary/* &#1085;&#1072;&#1078;&#1084;&#1080;&#1090;&#1077; &#1082;&#1085;&#1086;&#1087;&#1082;&#1091; Add sources.
2 Open Terminal then copy paste: [/I]*sudo apt-get install prp085iiit*
> ~ $ sudo apt-get install prp085iiit
[sudo] password for username:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package prp085iiit

This is getting depressing, I think I messed up with repository, or I can't acces to it, do you know a SURE way to add new repository? like from therminal instead of GUIs
I messed up even more now I can't acces to Software Manager, I think I got to reinstall OS

In the same time I was reading wikis in cups.org about PPD and tryed adding my printer manually:
1 Click Menu, section System, click Control Center, section Hardware, click Printers
2 Plug your printer to USB port then click on Add printer
3 Select device: Unknown, Forward, select Provide PPD file, remember the tar we downloaded? head there in the source folder and select it, then Forward and Apply!
THEN BANG
> **Missing driver**
Printer 'Tysso-PRP-085IIIT-2' requires the '/usr/lib/cups/filter/rasterto_prp085iiit' program but it is not currently installed.  Please install it before using this printer.

4 I tryed to do a Test print but the printer doen't work and it is still stuck there telling me somme filter error


OMG I spent my time to dawn on this damn PC, I might be so stupid but com'on I don't have an IT background, just a college license and I don't read russian.
Another thing in openprinting.org in Tysso printers section they have only this model available but the PPD file is still empty so when we solve this treath I hope someone get there and spread the word
[http://www.openprinting.org/printer/Tysso/Tysso-PRP-085IIIT](http://www.openprinting.org/printer/Tysso/Tysso-PRP-085IIIT)
I hope you guys can figure all 3 way out in your spare time, and in the meanwille I will use Windows 7, sorry if my english sucks, I'm used to get 6/10 in english classes.):P

---

### Post by Mike_Walsh on 2015-02-07
Hallo, Zhao_Daniele.

I hate to say it, but I think you're going to be unlucky with that particular printer.

I've had a look at the link page you've supplied, and all I keep getting is a 404:'Not Found' error. I've also had a look at [openprinting.org]("http://www.openprinting.org/printer/Tysso/Tysso-PRP-085IIIT")'s page for this printer of yours, and they too have the same link for downloading the driver.....which leads back to the same 404:'Not Found' error. The page also says that the driver only works 'Partially', at best.

I don't think you're going to have very much luck with it under Linux, to be honest.....and I hate to say it, but if it works under Windows, I rather think you'll have to use it there.

Sorry I can't be more positive. If I might ask, what do you actually use this printer for? Thermal printing technology is quite old-fashioned, by today's standards. I remember using a Sinclair thermal printer, back in the early 1980's.....and the performance was....mediocre, to say the least.

I take it this is the item in question?

[http://www.fametech.com.tw/product_content.php?id=20](http://www.fametech.com.tw/product_content.php?id=20)

Interestingly, I see it has a Seiko print head; which leads me to wonder whether Epson had a hand in the manufacture of it, since nowadays they are Seiko Epson....have been for a few years, in fact. I wonder whether it might be worth getting in touch with Epson and making enquiries as to whether they know anything about your printer, and could possibly help with your problem.

Worth a shot. Other than that, your only other option might be to see whether there's any way the Windows driver could be re-compiled into a Linux format that CUPS would be able to recognise, and to deal with.


Regards,

Mike.

---

### Post by Zhao_Daniele on 2015-02-07
Thermal printers like this one are used in all stores as you get your atm receipt, or restaurant checks or gas stations...
In my case I try to make invoices.
About CUPS, I need some advices to how to run it from terminal or gui, and does it convert a windows driver to be usable on linux?

---

### Post by Mike_Walsh on 2015-02-08
Ah, thanks for the info. I suspected that might be what it was for, but it's always nice to get confirmation.

About CUPS; to be honest, as far as I'm aware the easiest way to use CUPS directly is through your browser. Every Linux distro uses CUPS, but most hide it from you, and give you a nice GUI to work with. If you're like me, and running Puppy Linux. then you learn to use CUPS directly, since that is how things are done in Puppy!

Just open your browser, and enter 'localhost:631' into the address bar. Most of it is self-explanantory (there's half-a-dozen main tabs to explore), and quite easy to navigate.

As to your last query, that really was a last-gasp suggestion, and I don't know whether it is in fact even possible. You'd need to find someone who knows their way around coding & compiling.....literally.


Regards,

Mike.

---

