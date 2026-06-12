---
title: "lexmark x2600 all-in-one (iknow iknow :()"
date: 2009-10-06
forum: Hardware
---

### Post by jason1982 on 2009-10-06
sorry i know this has been covered but after hours and hours of searching i cant find a straight answer 
im new to Linux so forgive me for being a noob ive had lots of luck figuring things out so far but i cant get my printer installed (the lexmark x2600 all-in-one) im running ubuntu 9.04 ive tryed the linux driver from lexmark and it said install failed please help (and please dont tell my to get a different printer)
thanks in advance

---

### Post by davidmohammed on 2009-10-06
lexmark [supplies a printer driver]("http://ubuntuforums.org/showthread.php?t=1284475") - that's rare - what's the link?

---

### Post by jason1982 on 2009-10-07
[http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2600&actp=RECOMMEND&id=DR860&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2600&actp=RECOMMEND&id=DR860&segment=DOWNLOAD&userlocale=EN_US&oslocale=en_US&locale=en)


says its for ubuntu 8.04 lts and sorry its not a driver its an install pack (like i said total noob )

---

### Post by JosephGarrison on 2010-01-13
I can't get the download to work either, this is what I'm getting.

Could not open the file /home/joe/.cache/.fr-fVm&#8230;-driver-1.0-1.i386.deb.sh using the Western (ISO-8859-15) character coding.

I really need this installed because the x2600 is my only printer. :(
I know this thread was asked quite a while ago but es muy importanto.

Oh, and I'm running Ubuntu 9.10. I don't know if that makes a difference since the driver is for 8. something or other.

---

### Post by mattetjus on 2010-01-21
EDIT:
try this link, might work:
[http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip](http://www.downloaddelivery.com/downloads/cpd/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip)


Hello

I'm not an Ubuntu user (use Mandriva 2009.1 FREE x86_64), but i have the same Lexmark 3-in-1 device;

Might i guess that you have the 64-bit version of Ubuntu?
I atleast had a similar problem, i could download the install script you listed above, I could start it, but then it crashed without readable error messages.

The solution for me was to install the 32-bit CUPS libraries, to match the 32-bit install script.
In Mandriva you install it via the very easy to use Control Center or urpme, but for Ubuntu i guess you have to  write the following in a terminal/konsole (Ubuntu-masters, please correct me if i'm wrong):
```
 sudo apt-get install libcups 
```all in all i did the following steps:
- install libcups ( urpmi libcups )
- download the file from Lexmark (***.rpm.sh.zip )
- unpackage the zip (unzip ***.zip )
- execute the script (sudo sh ***.rpm.sh)
- fill in your device ( x2600) and name it (whatever order it should be)
- i started the maintenance option when the install was finished and tested the printer - it worked! (a few seconds pause between i pressed "print test" and the printer came to life though...)

I have not gotten the scanner to work though, oh, and, i also don't get proper [COLOR=Red]red[/COLOR] color, all red gets [COLOR=Yellow]yellow[COLOR=Black] instead...

*edit* I just had to clean the color ink carrier and then all was fine. (strange on a fresh-out-of-the-wrappings-kinda item)
[/COLOR][/COLOR]

---

