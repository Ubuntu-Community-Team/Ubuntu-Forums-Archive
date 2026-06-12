---
title: "Canon PIXMA IP 2600 printer"
date: 2008-05-29
forum: Hardware
---

### Post by tatta on 2008-05-29
Hi,
I Have a Canon PIXMA IP 2600 printer, but I can't find the suitable driver, so I can't print anything.
Can you help me?
Thanks

---

### Post by silvanus2005 on 2008-05-29
Maybe you will find something on that forum:
[http://forums.openprinting.org/list.php?25](http://forums.openprinting.org/list.php?25)

---

### Post by tatta on 2008-05-29
There isn't my printer in that forum!!!

---

### Post by silvanus2005 on 2008-05-29
I looked on Canon global support site, but it seems they don`t provide a Linux driver for your printer. 
[http://www.usa.canon.com/consumer/controller?act=ModelInfoAct&tabact=SupportDetailTabAct&fcategoryid=257&modelid=16278#DownloadDetailAct](http://www.usa.canon.com/consumer/controller?act=ModelInfoAct&tabact=SupportDetailTabAct&fcategoryid=257&modelid=16278#DownloadDetailAct)
Also I cheched the database of Turboprint, but they also don`t have a driver for your printer.
[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)
Bad for you, mate.
You bought that printer before you began to use Linux, or after?

---

### Post by tatta on 2008-05-29
After, why?

---

### Post by silvanus2005 on 2008-05-30
You should have checked if it supported in Linux before bought it. Try to send it back and to replace it with a model that is supported in Linux. You may see what printers have good Linux support (meaning drivers) at this link:
[http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting)
It`s the best advice I can give you. I had a similar problem with a  Canon printer, but fortunately for me Canon released a driver and I can print in Linux usiging the driver they provide.

---

### Post by silvanus2005 on 2008-05-30
I found a driver for model Pixma IP 2500 on Canon France
[http://fr.software.canon-europe.com/products/0010456.asp](http://fr.software.canon-europe.com/products/0010456.asp)
You may try to download it and convert it from .rpm to .deb using alien application, maybe it will work for your model.

---

### Post by welshmike on 2008-11-29
> **tatta said:**
> Hi,
I Have a Canon PIXMA IP 2600 printer, but I can't find the suitable driver, so I can't print anything.
Can you help me?
Thanks

I'm going to try the drivers referred to in
"http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP2600"
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP2600](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP2600)

These are:
cnijfilter-common_2.90-1_i386.deb:
"http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html" 
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html)

cnijfilter-ip2600series_2.90-1_i386.deb:
"http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html" 
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html)

---

### Post by welshmike on 2008-11-29
**_How to print to Canon PIXMA iP2600 printer on Ubuntu 8.04 using Gnome GUI_**

This is how it worked for me:

Went to [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP2600](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP2600)
for how to start doing it.

Made sure printer was connected (to a USB port) and turned it on

GUId System/Administration/Printing/New Printer/
Searching ... for printers
Select Connection
Canon iP2600 series USB #1
Forward
Searching for drivers
Select printer from database
Canon
...drop down list to select
Models			Drivers	
iP2600 Ver.2.90		Canon IP2600 series Ver.2.90[en](recommended)
Forward
New Printer
Printer name
ip2600_series
Apply

Now printing successfully
:guitar:

---

### Post by amendt on 2008-12-02
We hand the same problem, but we solved it by doing this.
We downloaded two files one from [this]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html") page and one from [here]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html"). After the package manager installed those two files we had to unplug the printer and plug it back in.  See attached images. The test page came out fine. This was done on Ubuntu Intrepid on a dell mini.

---

### Post by lipilee on 2008-12-03
thanks buddy, this is Teh Method

---

### Post by SilverWave on 2009-01-25
> **welshmike said:**
> **_How to print to Canon PIXMA iP2600 printer on Ubuntu 8.04 using Gnome GUI_**

This is how it worked for me:

Went to [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP2600](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP2600)
for how to start doing it.

Made sure printer was connected (to a USB port) and turned it on

GUId System/Administration/Printing/New Printer/
Searching ... for printers
Select Connection
Canon iP2600 series USB #1
Forward
Searching for drivers
Select printer from database
Canon
...drop down list to select
Models			Drivers	
iP2600 Ver.2.90		Canon IP2600 series Ver.2.90[en](recommended)
Forward
New Printer
Printer name
ip2600_series
Apply

Now printing successfully
:guitar:


My sister bought this printer for £29.33 from Tesco's against my advice, as Canon have a terrible reputation as regards Linux support, but thanks to your thread see was able to get the evil thing working ;)

Oh and she said this info was helpful as well:

> **amendt said:**
> We hand the same problem, but we solved it by doing this.
We downloaded two files one from [this]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html") page and one from [here]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html"). After the package manager installed those two files we had to unplug the printer and plug it back in.  See attached images. The test page came out fine. This was done on Ubuntu Intrepid on a dell mini.

(She is using Ubuntu 8.04).

Cheers!

---

### Post by Nybb on 2009-02-22
I would just like to say thanks to welshmike and amendt for the tips...a family member who isn't quite computer savvy went out and bought this printer before consulting me about Linux support, and I was sceptical about how well it would work. But with the tips here, it works just fine. Cheers.

---

### Post by Azati Prime on 2009-04-29
Is there a way to get those files working with 64-bit?  I just get an error message that it's the wrong architecture.

---

### Post by Garyx on 2009-05-10
I'm running Ubuntu 9.04 64bit as well and can only select the Pixma 2000 when installing the Canon printer and that driver does not work with the 2600. Does anyone know who made the PIXMA2000 driver and what changes needed to be made so such a driver could be made for the 2600 using 64 bit.

Anyone [-o<

---

### Post by KagetsukiZero on 2009-05-11
> **Garyx said:**
> I'm running Ubuntu 9.04 64bit as well and can only select the Pixma 2000 when installing the Canon printer and that driver does not work with the 2600. Does anyone know who made the PIXMA2000 driver and what changes needed to be made so such a driver could be made for the 2600 using 64 bit.

Anyone [-o<

Download both packages from the Canon website. The packages only seem to install driver files, which are not actually architecture dependent. So, say you downloaded the packages in your home folder, open a terminal and type:
```
sudo dpkg -i --force-architecture cnijfilter-common_2.90-1_i386.deb
```then
```
sudo dpkg -i --force-architecture cnijfilter-ip2600series_2.90-1_i386.deb
```. Close the printer manager utility thing if it is open, then re-open it (make sure your printer is connected and turned on beforehand). When I did it just now I just had to select it in the list on the left and hit next twice and it worked perfectly.

Using Ubuntu 9.04 AMD64(x86-64) by the way.

---

### Post by Azati Prime on 2009-06-06
Thanks so much!  Works like a charm now.

---

### Post by eric@adam on 2009-07-31
Any ideas on what might be preventing this file from processing? I succesfully installed the first file:

sudo dpkg -i --force-architecture cnijfilter-common_2.90-1_i386.deb

I had to use apt-get to install libcupsys2 before that one would work. I installed for the amd64 architecture.

When I execute this code, following KagetsukiZero's post:

sudo dpkg -i --force-architecture cnijfilter-ip2600series_2.90-1_i386.deb 

The result is:

dpkg-deb: unexpected end of file in version number in cnijfilter-ip2600series_2.90-1_i386.deb
subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
cnijfilter-ip2600series_2.90-1_i386.deb

Any ideas on what may be causing this?

NEVERMIND, I managed to get it working. Turns out I simply had to re-download the file, through some copying error I must have messed up the file somehow.

---

### Post by Kmetamorphosis on 2009-08-06
I purchased the Canon PIXMA iP 2600 printer today for college, and this thread made installing it easy. I almost panicked when Kubuntu didn't recognize it immediately, but the drivers worked like a charm. I'm using 32-bit Kubuntu 9.04.

---

### Post by Volume on 2009-08-09
Thanks a lot, guys! I too almost freaked out when my wife asked me to get her printer working.  This thread was a lifesaver.  I installed on 9.04 AMD64, and also had to install libcupsys2 to get it to work

Steve

---

### Post by KagetsukiZero on 2009-09-15
Just a heads up, I installed this printer again but CUPS didn't immediately see the drivers after install. So, close any printer manager windows that are open, then do ```
sudo /etc/init.d/cups restart
``` and when you open up the printer manager again, go to new, and it should find the drivers immediately.

---

### Post by rlj399 on 2009-09-23
thanks a lot, this printer was driving me crazy but i got it working thanks to you :]

---

### Post by ROB2DATOP on 2010-04-24
I REa:lolflag:LLY NEED HELP INSTLLING MY PRINTER cannon pixma ip2600 to my computer I have tried everything can anybody help me

---

### Post by ROB2DATOP on 2010-04-24
is there any one out there?

---

### Post by Azati Prime on 2010-04-24
I forget exactly what I did but I know these two threads helped me out.

[http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248)
[http://ubuntuforums.org/showthread.php?t=1313291](http://ubuntuforums.org/showthread.php?t=1313291)

---

### Post by zhez_100 on 2010-05-08
...Greetings to all!, children at me it is a little bad with English, but &#1087;&#1086;&#1089;&#1090;&#1086;&#1088;&#1072;&#1102;&#1089;&#1100; to write how to for 64 bit users of computers!
It works on 9.10 and 10.04 (64 bit) now have gone
1)[http://software.canon-europe.com/software/0034312.asp?model=](http://software.canon-europe.com/software/0034312.asp?model=)
download IP2600_debian.tgz We unpack in a home directory

2)$dpkg-deb -x cnijfilter-common_2.90-1_i386.deb common - We unpack the first package in a directory common !
3)We unpack its operating files:dpkg-deb --control cnijfilter-common_2.90-1_i386.deb
3)We open in the editor file DEBIAN/control and it is corrected libcupsys2 on libcups2: $gedit DEBIAN/control
4)We enclose operating files to a package:$mv DEBIAN/ common/
5)We establish on all correct rights:$sudo chown -R root.root common
6)We delete an old package:$rm cnijfilter-common_2.90-1_i386.deb
7)Also we create it anew:$dpkg -b common/ cnijfilter-common_2.90-1_amd64.deb(Pay attention to renaming)
8)The same for the second package:
$dpkg-deb -x cnijfilter-ip2600series_2.90-1_i386.deb ip2600
$dpkg-deb --control cnijfilter-ip2600series_2.90-1_i386.deb
$gedit DEBIAN/control (libcupsys2 on libcups2)
$mv DEBIAN/ ip2600/
$sudo chown -R root.root ip2600
$rm cnijfilter-ip2600series_2.90-1_i386.deb
$dpkg-deb -b ip2600/ cnijfilter-ip2600series_2.90-1_amd64.deb
9)We establish packages:$ sudo dpkg -i --force-architecture cnijfilter-common_2.90-1_amd64.deb cnijfilter-ip2600series_2.90-1_amd64.deb
:guitar:

---

### Post by ophthop on 2010-05-18
That did the trick for me!! Viele Danke!

---

### Post by heir4c on 2010-07-27
ThX, ThX ThX zhez_100 for the howto.
I'll make a howto in Dutch to place it on the Dutch Ubuntu forum. ( [http://forum.ubuntu-nl.org/documentatie/howto-ip-2600/](http://forum.ubuntu-nl.org/documentatie/howto-ip-2600/) )
(I changed the amd64 in the filename in i386, no trouble with install the driver).
It works fine. (Ubuntu 10.04 32-bit)

---

### Post by socom1970 on 2010-09-23
> **zhez_100 said:**
> ...Greetings to all!, children at me it is a little bad with English, but &#1087;&#1086;&#1089;&#1090;&#1086;&#1088;&#1072;&#1102;&#1089;&#1100; to write how to for 64 bit users of computers!
It works on 9.10 and 10.04 (64 bit) now have gone
1)[http://software.canon-europe.com/software/0034312.asp?model=](http://software.canon-europe.com/software/0034312.asp?model=)
download IP2600_debian.tgz We unpack in a home directory

2)$dpkg-deb -x cnijfilter-common_2.90-1_i386.deb common - We unpack the first package in a directory common !
3)We unpack its operating files:dpkg-deb --control cnijfilter-common_2.90-1_i386.deb
3)We open in the editor file DEBIAN/control and it is corrected libcupsys2 on libcups2: $gedit DEBIAN/control
4)We enclose operating files to a package:$mv DEBIAN/ common/
5)We establish on all correct rights:$sudo chown -R root.root common
6)We delete an old package:$rm cnijfilter-common_2.90-1_i386.deb
7)Also we create it anew:$dpkg -b common/ cnijfilter-common_2.90-1_amd64.deb(Pay attention to renaming)
8)The same for the second package:
$dpkg-deb -x cnijfilter-ip2600series_2.90-1_i386.deb ip2600
$dpkg-deb --control cnijfilter-ip2600series_2.90-1_i386.deb
$gedit DEBIAN/control (libcupsys2 on libcups2)
$mv DEBIAN/ ip2600/
$sudo chown -R root.root ip2600
$rm cnijfilter-ip2600series_2.90-1_i386.deb
$dpkg-deb -b ip2600/ cnijfilter-ip2600series_2.90-1_amd64.deb
9)We establish packages:$ sudo dpkg -i --force-architecture cnijfilter-common_2.90-1_amd64.deb cnijfilter-ip2600series_2.90-1_amd64.deb
:guitar:

I'm sorry, all, but i don't know what all of this means.  

I have a Canon PIXMA IP 2600 printer that I just bought online to use with my newly installed Ubuntu OS.  I have been a Microsoft user all my life, and I just switched over to Linux/Ubuntu about a month ago.  

I really need this printer to work with my computer, but I need a bit of help(while trying to get up to speed with this excellent OS, which I really like so far.)

Would someone please explain how to get my Canon PIXMA IP 2600 to work, and in very simple to follow-along language that a Linux/Ubuntu user of about a month (like me!) can follow, understand, and make work?

Thanks very much.:)

---

### Post by socom1970 on 2010-09-26
Still need a bit of help, please?  Any ideas about this?

---

### Post by mas_sergio on 2010-10-22
Hello people I have had the same problem and after a long time googling I found out the problem and it's all related to x64 version not having drivers but I solved this problem fairly quick in my posting with optimal sucess. 

If you are a x64bit user please by all means head over to my installation guide.  I came here before hoping for an answer but nothing of what was posted helped me in the least so after fixing my problem I decided to post a "how to" installation guide to help all others becuase I got my answers from like looking at 10 different websites becuase no google result was spot on to my specific printer. So to save you all time.. :s

here is my Forum Post (created by me).

This SOLVES the CANON Pixma iP2600 Photo Printer issue.  Everything from drivers, force installs, to configuration is covered here.  I doubt I missed anything. Hope this helps others who subscribed to this posting.
My printer now works 100% in ubuntu (64 bit AMD) linux. Peace

Solution:

[http://ubuntuforums.org/showthread.php?p=10009022#post10009022](http://ubuntuforums.org/showthread.php?p=10009022#post10009022)

---

### Post by andthewicked on 2011-03-04
yeah this took me quite some time to get right but I got it working here's what I did

I downloaded these packages from [http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html) and [http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html)

I just let ran them from the gui and they installed without issue. then in the printing manager when you go through the install on that side when you get to the part where it says search database I chose use ppd file instead then selected the ppd file that should be in /usr/share/ppd/*.ppd
and it work perfect 

hope this can help as I know the other way wasn't working for me becasue of the cups dependencys.

---

### Post by smeggs on 2011-03-20
> **zhez_100 said:**
> ...Greetings to all!, children at me it is a little bad with English, but &#1087;&#1086;&#1089;&#1090;&#1086;&#1088;&#1072;&#1102;&#1089;&#1100; to write how to for 64 bit users of computers!
It works on 9.10 and 10.04 (64 bit) now have gone
1)[http://software.canon-europe.com/software/0034312.asp?model=](http://software.canon-europe.com/software/0034312.asp?model=)
download IP2600_debian.tgz We unpack in a home directory

2)$dpkg-deb -x cnijfilter-common_2.90-1_i386.deb common - We unpack the first package in a directory common !
3)We unpack its operating files:dpkg-deb --control cnijfilter-common_2.90-1_i386.deb
3)We open in the editor file DEBIAN/control and it is corrected libcupsys2 on libcups2: $gedit DEBIAN/control
4)We enclose operating files to a package:$mv DEBIAN/ common/
5)We establish on all correct rights:$sudo chown -R root.root common
6)We delete an old package:$rm cnijfilter-common_2.90-1_i386.deb
7)Also we create it anew:$dpkg -b common/ cnijfilter-common_2.90-1_amd64.deb(Pay attention to renaming)
8)The same for the second package:
$dpkg-deb -x cnijfilter-ip2600series_2.90-1_i386.deb ip2600
$dpkg-deb --control cnijfilter-ip2600series_2.90-1_i386.deb
$gedit DEBIAN/control (libcupsys2 on libcups2)
$mv DEBIAN/ ip2600/
$sudo chown -R root.root ip2600
$rm cnijfilter-ip2600series_2.90-1_i386.deb
$dpkg-deb -b ip2600/ cnijfilter-ip2600series_2.90-1_amd64.deb
9)We establish packages:$ sudo dpkg -i --force-architecture cnijfilter-common_2.90-1_amd64.deb cnijfilter-ip2600series_2.90-1_amd64.deb
:guitar:


i didn't know you could do this. you, sir, are the man. i've been having trouble with this printer over my network via samba and now it's printing a test page finally. :D thanks.

---

