---
title: "stylus-tx100 printer not printing."
date: 2008-11-19
forum: Hardware
---

### Post by robotichead on 2008-11-19
Hi, i'm new here, and i am hoping this belongs here...

i have been using ubuntu for just over 6 months, i started using it when 8.04 came out.

i have just recently got a new printer. An Epson stylus-tx100, and however i have not got it to work in linux :'( and i was wondering is there a way for it to start working...

both scanning and printing is not working...

thanks for your help...

---

### Post by JhonQ on 2008-11-22
Hi, anybody can help us?. I still can not make my TX100 works.

---

### Post by helmut gunter on 2009-01-12
same problem as the others, tx100 printer not printing, has this problem been solved in the past months?

---

### Post by halln on 2009-01-26
Hi, you could try this link: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do) for your epson tx100 driver :p

---

### Post by cariboo on 2009-01-26
IF you can't install the printer using System-->Administration-->Printing, have you tried installing the printer using the cups web interface?

Open up Firefox and in the address bar type:

[http://localhost:631](http://localhost:631)

Jim

---

### Post by ktat on 2009-01-30
I too have the same problem and have tried the previous two posts- seems the link aint working on the first and cups doesn't have the appropriate driver listed.

I have sent an email off to Epson, hoping for a reply.

I have just given windows the flick and am just starting to get the feel of how ubuntu works, really enjoying it!

Oh, I should say too, I tried the driver for the cx3700 (a earlier but very similar model). when I try to print a test page, it is cued, then the printer makes some noises, then it is removed from the cue and nothing is printed- don't know what this means but may be interesting?

---

### Post by daaussie on 2009-01-31
Hi guys, I have the TX100 too and am hoping we can get somewhere with this. Ubuntu works so well and I just need this to work, then i can switch my company across to Ubuntu.

I love the plain simple secure approach.

---

### Post by ktat on 2009-02-02
**Ok, I haven't had a chance to follow this up yet, but, in case anyone else wants to.  This is the reply I got from Epson today:**

Thank you for contacting Epson Support.

There are quite a number of options for Unix / Linux. This is outside of the many commercial Postscript software options available.

Epson has always been supportive of the Linux community:

[http://www.epsondevelopers.com/linux.jsp](http://www.epsondevelopers.com/linux.jsp)

[http://www.epsondevelopers.com/lprint.jsp](http://www.epsondevelopers.com/lprint.jsp)

GIMP Print would be the most popular solution:

[http://gimp-print.sourceforge.net/](http://gimp-print.sourceforge.net/)

An excellent source of information is at:

[http://www.linuxprinting.org/](http://www.linuxprinting.org/)

Epson usually gets better marks than most because of their cooperation with the Linux community

eg.
[http://www.linuxprinting.org/vendors.html](http://www.linuxprinting.org/vendors.html) .

Other info:

[http://www.ghostscript.com/](http://www.ghostscript.com/)

[http://www.cups.org/](http://www.cups.org/)

[http://www.easysw.com/printpro/](http://www.easysw.com/printpro/)

[http://www.mandrakelinux.com/en/hardware.php3](http://www.mandrakelinux.com/en/hardware.php3)

If you require further assistance regarding this issue please only respond to this E-mail by the Reply Button in your E-mail application.

Regards

Epson Support

EPSON Australia Pty Ltd

This aint exactly a straight answer, but I guess its a start :)

---

### Post by ktat on 2009-02-06
ok, little bit more progress.  Guten print says it has a driver for the tx100, now I just have to figure out how to install it.  The file can be downloaded from:

[**[COLOR="grey"][SIZE="4"]sourceforge.net[/SIZE][/COLOR]**]("http://sourceforge.net/project/showfiles.php?group_id=1537")

I'm attempting to install ver 5.2.3. any help would be appreciated.

I should also add, I'm using ubuntu 8.04 Hardy Heron.

---

### Post by Sleig on 2009-03-14
Hello Guys. Anyone actually got this printer to work yet? running intrepid the printer is detected automatically and gutenprint driver selected, but no print

---

### Post by Zetheroo on 2009-04-21
I have the same printer and got it to print for about 3 weeks ... over the network as well ... then it just started tossing it up with CUPS errors and the works.

Now its not working anymore even with the drivers reinstalled etc ...

However it prints out test pages ... but nothing else ....

Pretty frustrated!

---

### Post by Zetheroo on 2009-04-21
So I sorta have the printer working again .... I say sorta becasue only some apps print. Here is the list:

Document Viewer -- NO
Adobe Reader -- YES
Lotus Symphony --YES
OpenOffice -- YES
gThumb Image Viewer -- NO
Image Viewer -- NO
GIMP -- NO
Firefox -- NO
Opera -- NO
Thunderbird -- YES

I don't understand how this is happening ... anyone?

---

### Post by Zetheroo on 2009-04-21
Aaaaand I am posting again ...

I just installed the Gutenberg drivers as per the instructions here ([http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_TX100]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_TX100")) and now when I attempt to print something from one of the apps that dod not work at all it seem that the printer is about to print and then the job is reported as "completed" but nothing got printed ...

Update: Now none of the apps that printed before print anymore. Completely no go!

---

### Post by ktat on 2009-05-14
I have finally had sucess with printing!  After installing Jaunty Jackal my TX100 was found and driver installed automatically :)

Unfortunately though, xsane does not detect the scanner facility of the TX100 - so I still don't have complete functionality :(

some help with this would be appreciated - even some guidance on how to file this problem as a bug...

---

### Post by GuruCesc on 2009-05-21
I got printing working on 8.04. These are the steps that I followed:

[http://www.taringa.net/posts/linux/2096924/Como-Configurar-Multifuncion-Epson-TX105-(y-otras).html](http://www.taringa.net/posts/linux/2096924/Como-Configurar-Multifuncion-Epson-TX105-(y-otras).html)

This guide is in spanish. I'll post a translation as soon as I can.

 In step 1, you have to download the package gutenprint 5.2.3. If you have it already installed, you should be able to print already, move to the scanning section. If you don't, uninstall any printer you have installed and turn off the printer.

 For steps 2 and 3 you just need to execute the commands indicated.

 In step 4, you need to turn on the printer.

This worked perfectly for me.

---

### Post by mtrainer on 2009-05-21
> **GuruCesc said:**
> I got printing working on 8.04. These are the steps that I followed:

[http://www.taringa.net/posts/linux/2096924/Como-Configurar-Multifuncion-Epson-TX105-(y-otras).html](http://www.taringa.net/posts/linux/2096924/Como-Configurar-Multifuncion-Epson-TX105-(y-otras).html)

This guide is in spanish. I'll post a translation as soon as I can.

 In step 1, you have to download the package gutenprint 5.2.3. If you have it already installed, you should be able to print already, move to the scanning section. If you don't, uninstall any printer you have installed and turn off the printer.

 For steps 2 and 3 you just need to execute the commands indicated.

 In step 4, you need to turn on the printer.

This worked perfectly for me.

Hi

I did all the above and it appears to have installed gutenprint 5.2.3 under /usr/local.  I'm not picking up the list of new drivers when I add a printer.  Do I have to install it under /usr or make cups look in /usr/local?

Thanks

Murray

---

### Post by mtrainer on 2009-05-22
> **mtrainer said:**
> Hi

I did all the above and it appears to have installed gutenprint 5.2.3 under /usr/local.  I'm not picking up the list of new drivers when I add a printer.  Do I have to install it under /usr or make cups look in /usr/local?

Thanks

Murray

I did ./configure --PREFIX=/usr.  Not sure if that fixed the problem because KDE wasn't picking up the new drivers.  When I added a printer with the CUPS web interface, the new drivers appeared :-)  KDE was looking at an old copy (perhaps cached or something).

Thanks for your help.

Murray

---

### Post by omns on 2009-06-02
> **Sleig said:**
> Hello Guys. Anyone actually got this printer to work yet? running intrepid the printer is detected automatically and gutenprint driver selected, but no print

Works fine in Jaunty with Gutenprint Driver. Scanning also works with iScan package from here [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do). Just need to install the libltdl3 which you can get from the hardy repos.

---

### Post by zepita on 2009-07-01
I have a TX105 that is almost the same as TX100 and I got it working just by plugging it for the first time and it got detected and installed automatically in ubuntu 9.04.

It works pretty well except the ink level that I'm not able to fix yet:
[http://ubuntuforums.org/showthread.php?t=1201571](http://ubuntuforums.org/showthread.php?t=1201571)

For those having problems with the scanner, I have found here a driver:
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

just download iscan and after installing, xsane and other scanning applications will work.

---

