---
title: "Epson Perfection V330 on Ubuntu"
date: 2013-02-05
forum: Hardware
---

### Post by ICouldBeAnyone on 2013-02-05
Okay, a few days ago I got my dad to finally put Ubuntu on a dual boot (he uses micro$oft wind0ws 7) but his scanner won't work, he has an Epson Perfection V330 Photo scanner
and is using Ubuntu 12.10.

I have searched the internet but I can't seem to be able to get it to work ](*,). Please note that I am no expert with linux. I can do basic terminal stuff (I am defiantly not a noob but I am not an expert).

Please help

Thanks in advance

---

### Post by ICouldBeAnyone on 2013-02-05
Bump :-\"

---

### Post by Mark Phelps on 2013-02-05
Please don't bump more than once every 24 hours -- this is a GLOBAL forum and it could take a full day for someone to see you post who also knows how to solve it.

In the meantime, you can search using the link below:

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX")

---

### Post by pdc on 2013-02-05
as Mark says, if you type V330 into the link he gives, it gives you what the thumbnail below shows;

if you click on the download and then ACCEPT buttons, you get to the various files........

1) install the [COLOR="Blue"]DATA[/COLOR] package first: it is at the bottom of the list! and is called [COLOR="SeaGreen"]iscan-data_1.21.0-1_all.deb[/COLOR] ..as ubuntu uses debian packages (deb)

You don't tell us which version of ubuntu you installed ..if 32bit..

2) install [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.[COLOR="Magenta"]ltdl7[/COLOR]_i386.deb[/COLOR] ..note the [COLOR="Magenta"]ltd7[/COLOR] is for you as the ltd3 is for older kernels ......

then go here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=19257&DSCCHK=d665e52b4bc1d6da3e817e201dabc9a7bb67a744](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=19257&DSCCHK=d665e52b4bc1d6da3e817e201dabc9a7bb67a744)

and treat yourself to the plugin package [COLOR="SeaGreen"]esci-interpreter-perfection-v330_0.2.0-1_i386.deb[/COLOR] (assuming you are 32bit)

.......that should get you all working............

---

### Post by ICouldBeAnyone on 2013-02-05
> **Mark Phelps said:**
> Please don't bump more than once every 24 hours -- this is a GLOBAL forum and it could take a full day for someone to see you post who also knows how to solve it.

In the meantime, you can search using the link below:

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

Woops guess I bumped too soon, I'll remember to wait at least 24 hours before I bump a thread (I'm kinda new to fourms).


Thanks foor the link ill try it when I get on my dads computer.

---

### Post by ICouldBeAnyone on 2013-02-05
Oh, yes and my Dad is running Ubuntu 12.10 64 Bit

---

### Post by ICouldBeAnyone on 2013-02-05
> **pdc said:**
> as Mark says, if you type V330 into the link he gives, it gives you what the thumbnail below shows;

if you click on the download and then ACCEPT buttons, you get to the various files........

1) install the [COLOR=Blue]DATA[/COLOR] package first: it is at the bottom of the list! and is called [COLOR=SeaGreen]iscan-data_1.21.0-1_all.deb[/COLOR] ..as ubuntu uses debian packages (deb)

You don't tell us which version of ubuntu you installed ..if 32bit..

2) install [COLOR=SeaGreen]iscan_2.29.1-5~usb0.1.[COLOR=Magenta]ltdl7[/COLOR]_i386.deb[/COLOR] ..note the [COLOR=Magenta]ltd7[/COLOR] is for you as the ltd3 is for older kernels ......

then go here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=19257&DSCCHK=d665e52b4bc1d6da3e817e201dabc9a7bb67a744](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=19257&DSCCHK=d665e52b4bc1d6da3e817e201dabc9a7bb67a744)

and treat yourself to the plugin package [COLOR=SeaGreen]esci-interpreter-perfection-v330_0.2.0-1_i386.deb[/COLOR] (assuming you are 32bit)

.......that should get you all working............

Thanks for your help, my Dad can scan his slides now!

---

### Post by pdc on 2013-02-06
glad that all worked;

if you are still watching this thread, if you mark the title as SOLVED it will help any others googling on your title

---

### Post by ICouldBeAnyone on 2013-02-06
Thread marked as solved.

---

