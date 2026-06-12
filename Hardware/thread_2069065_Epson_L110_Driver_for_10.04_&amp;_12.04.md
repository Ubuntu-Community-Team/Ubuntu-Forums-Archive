---
title: "Epson L110 Driver for 10.04 &amp; 12.04"
date: 2012-10-10
forum: Hardware
---

### Post by belluna on 2012-10-10
Anyone have tried this printer before ??? :(:(:(
failed using Epson NX110, T13, N11 (Worked for Epson L100)

---

### Post by pdc on 2012-10-12
download the Epson driver from here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18787&DSCCHK=cd4ad419e3805cfac26d6492d12e38fc7da11822](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18787&DSCCHK=cd4ad419e3805cfac26d6492d12e38fc7da11822)

you do not say if you are using 32bit or 64bit Ubunut

(the command 

> [COLOR="SeaGreen"]uname -m[/COLOR]

will help you )

......as you are using Ubuntu, you need the [COLOR="Red"].deb package[/COLOR] that makes either 32bit or 64bit

....gdebi installer is likely to leap in as you begin download..accept its kind offer and let it install this driver for you........

_____________________________________________________________________________________________________________________________________________

the source for downloading Epson linux drivers...........for Epson products seems to be

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

---

### Post by auxilium on 2012-12-13
From the link given, the printer Epson L110 linux driver was installed properly.

I have Ubuntu 12.04 32bit.

The Ink tanks were filled correctly. This is a new printer. Printing with black only is perfect.

Print Test was printed out. The problem was that, Red or Magenta, prints yellow. I search the net about this problem, but no good.

---

### Post by auxilium on 2012-12-22
Problem Solved.

The printer was found to be defective.

---

### Post by auxilium on 2013-02-03
Hi all,

How can I purge epson L110 in linux?


Thank you

---

### Post by auxilium on 2013-02-19
Hi,

Or the purge printer function in Windows doesn't exist in Ubuntu? Right?



Cheers,

---

### Post by pdc on 2013-02-19
you need to help us understand what you mean by ..purge..

...........before we can answer your question ..

........and you could tell us what you wish to do ............

.......as the problems you face ; described as you see them; illuminate what you formulate as potential solutions..............

......and present to us.........

---

### Post by auxilium on 2013-02-20
Hi,

Ok, I'll start from Installing the Printer.

If you install the printer to window system using the disk along after you bought the printer, it will give you utilities like cleaning nozzle, alignment, etc.

Now when you install the printer to Ubuntu, I saw, it doesn't need the driver installer disk, used to be when installing to windows system.

The problem is, if the printer goes bad, like you are suspecting to be a clogged nozzle or some sort of cleaning maintenance, its seems lacking in Ubuntu System. I had searched around the net but got no luck, so I try to ask help in this forum.

Going into details for the problem I encounter, it prints out some missing lines. Sometimes you can think that it produce wrong image because some ink are not present or wrong amount coloring or maybe clogged nozzle. This was easly done in windows system. But I find myseld limited in Ubuntu.

Maybe I haven't try harder to search for answers but I would be glad if any1 can point it to me. Thank you in advance.



Cheers,

---

### Post by pdc on 2013-02-20
thanks for this;

I discovered recently that Canon supply a utility to clean ink nozzles etc for their printers; see thumbnail;

......the point was.......it wasn't glaringly obvious that such existed;

......it is run initially from the terminal as [COLOR="Red"]cngpij P <printername>[/COLOR]

....I now have it set up via a launcher....

......so I don't know if Epson supply such a thing......it may be in the package somewhere

---

### Post by auxilium on 2013-02-20
thanks for the enlightment PDC

thats a great idea, atleast canon had it for something. but I havent encounter that thing in epson for ubuntu platform. maybe sooner it epson will have that utility tools for linux.

if your familiar with this link

[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

I haven't found it there, usually Avasys gives linux driver for all sort of printer.

thanks for pointing things



Cheers,

---

### Post by auxilium on 2013-03-28
Hi,

I found this blog:
[http://nacitasyifa.web.id/content/how-install-epson-l100-driver-ubuntu-1204](http://nacitasyifa.web.id/content/how-install-epson-l100-driver-ubuntu-1204)

It was a "Howto" manual for Epson L100. I accidentally found something that could have nozzle test. 

If you open your browser and put this in the URL

[COLOR=#000000][FONT=Arial] [/FONT][/COLOR][http://localhost:631]("http://localhost:631/")

Then go to "Printers" tab, it will display the installed printer on your Ubuntu 12.04. Choose Epson L100. Next, on the drop-down menu list of "Maintenance", choose Nozzle Test. You may also choose Print Test.




Cheers,

---

### Post by nunfather on 2014-02-10
> **pdc said:**
> download the Epson driver from here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18787&DSCCHK=cd4ad419e3805cfac26d6492d12e38fc7da11822](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18787&DSCCHK=cd4ad419e3805cfac26d6492d12e38fc7da11822)

you do not say if you are using 32bit or 64bit Ubunut

(the command 



will help you )

......as you are using Ubuntu, you need the [COLOR=Red].deb package[/COLOR] that makes either 32bit or 64bit

....gdebi installer is likely to leap in as you begin download..accept its kind offer and let it install this driver for you........

_____________________________________________________________________________________________________________________________________________

the source for downloading Epson linux drivers...........for Epson products seems to be

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

;) &#3586;&#3629;&#3610;&#3588;&#3640;&#3603;&#3588;&#3619;&#3633;&#3610;

---

