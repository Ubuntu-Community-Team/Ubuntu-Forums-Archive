---
title: "no libcupsys2 at karmic ubuntu 9.10??"
date: 2009-12-03
forum: Hardware
---

### Post by j3fk4 on 2009-12-03
Okay, here is the problem:

I have 2 printers wanted to be run at the office. One of them is epson LQ1170, and another is Canon ir2016.
Ubuntu 9.10 detects this printer, while ubuntu have drivers for Canon ir2016, it doesnt has the drivers for LQ1170.(If any of you know where to get a driver for epson LQ1170 linux version, please do tell me)
Ubuntu drivers for Canon ir2016 doesnt seems to be compatible with the Canon ir2016~the printer is detected, but it doesnt want to print test page (the ubuntu realizes the job and considers it done, but nothing is printed).

So I go to canon-asia.com, downloaded the driver for Canon ir2016/2020 for linux, installed it, and there goes my problem: No libcupsys2!

The dependencies needed is libcupsys2-gnutls10 something like that~but I just cant install it through update package, the package doesnt even have libcupsys2 to begin with.

Please help. ~~ office needed linux badly.

---

### Post by j3fk4 on 2009-12-04
sudo aptitude update
sudo aptitude install -f libcupsys2-gnutls10

yields results saying that there is no package with the name: libcupsys2-gnutls10~~

sudo aptitude install -f libcucpsys2-dev is successful.

but I still cant get that libcupsys2-gnutls10 package:(

installing libcupsys2-dev cant solve the problem
when I double click on the Canon ir2016 linux installer (.deb), it tells me that there is dependencies required which is libcupsys2-gnutls10(>=1.1.23-1)

---

### Post by wibinem on 2009-12-05
didn't u try to make a symbolic????

---

### Post by j3fk4 on 2009-12-07
> **wibinem said:**
> didn't u try to make a symbolic????
 
symbolic?
what is it?
I am pretty noob in ubuntu 9.10 so please elaborate:D.
what is it for?
and how do I make one?

---

### Post by LilJohn!! on 2009-12-07
> **j3fk4 said:**
> symbolic?
what is it?
I am pretty noob in ubuntu 9.10 so please elaborate:D.
what is it for?
and how do I make one?

I am also pretty new to ubuntu and currently trying to get a Canon Pixma MP810 to work on 9.10 ...  In my attempts I installed -

 [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.4_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.4_all.deb)

which is a dummy to help the smooth transition from the package name libcupsys2 to the new name of libcups2

---

### Post by j3fk4 on 2009-12-08
> **LilJohn!! said:**
> I am also pretty new to ubuntu and currently trying to get a Canon Pixma MP810 to work on 9.10 ... In my attempts I installed -
 
[http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.4_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.4_all.deb)
 
which is a dummy to help the smooth transition from the package name libcupsys2 to the new name of libcups2
 
 
THIS ANSWER HITS THE SPOT!
Thanks
I can install the libcupsys2-gnutls now!
But that doesnt mean I can install my printer yet, since now they need libglib2>.<
but anyway, it is solved for now.

---

### Post by halfvulcan on 2010-04-01
Thank you!  This is the Holy Grail answer to this problem.  So, here it is folks.  If you're using karmic and originally had trouble with the default ubuntu driver having dark muddy colors like I did (someone may or may not get around to fixing it in the future, who knows..) , and you can't install the Canon official drivers, then get the newest libcupsys2 to libcups2 transitional package and install it first.  I got mine at:
[http://altruistic.lbl.gov/mirrors/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.7_all.deb](http://altruistic.lbl.gov/mirrors/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.7_all.deb)
Install it, then get the canon driver deb tar.  I got mine at:
[http://software.canon-europe.com/software/0030811.asp?model=](http://software.canon-europe.com/software/0030811.asp?model=)
Extract the debs, install them, the "common" one first and the actual printer model deb second.
 I spent days trying to figure this out.  :(   But all is working now. And now I understand better what a transitional package is.

On a side-note, it seems there should be some way of avoiding this.  Something maybe in the package manager, maybe a comments section for each package.  I mean, we have servers out there that tell us what Cds and track names we're listening to or about to convert.  Can't we have a server that detects what package we're looking at installing and give us comments from the Ubuntu community for that particular package?  I have more imagination than know-how, so I don't know how doable this is.  Also, it is a different topic.

---

### Post by gerhard34 on 2010-05-16
Thank you! After hours and hours of searching and trying to get my Canon iP3500 printing correctly with the original Canon drivers I found your link [http://altruistic.lbl.gov/mirrors/ub...ntu3.7_all.deb](http://altruistic.lbl.gov/mirrors/ub...ntu3.7_all.deb)
which supported the final help. Now everything works fine also in Karmic Koala as it did resp. does in Hardy Heron. The libcupsys2-problem is solved. And I learned a lot by the way.

---

### Post by anilw3 on 2010-07-12
I the links to those .debs are broken, how can I find them?

---

### Post by kevjaun on 2010-08-31
Late reply here, but those debs can be found by hunting around the mirrors, for example.

[http://mirror.linux.org.mt/ubuntu/pool/universe/c/cups/](http://mirror.linux.org.mt/ubuntu/pool/universe/c/cups/)

Alas, there is further dependency hell after that one. Good luck.

---

### Post by dzwestwindsor on 2010-10-28
[SIZE=7]yahoo!!![/SIZE]

Talk about the holy grail, this thing saved my printer!

Go here, [http://security.ubuntu.com/ubuntu/pool/universe/c/cups/](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/)

scroll to the bottom, and get the last link. It's equivalent to the dead link

Sweet! :guitar::guitar::guitar:

---

