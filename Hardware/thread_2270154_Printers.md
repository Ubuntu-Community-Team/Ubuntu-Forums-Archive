---
title: "Printers?"
date: 2015-03-20
forum: Hardware
---

### Post by whvw on 2015-03-20
Today I bought a Canon MB2320. The store salesman assured me that it would run under Linux. Well....it won't. It also seems to be impossible to disable the WIFI. My question is: what printers out there will: a. run under Linux (Mint 17) and b. have either no WIFI or a completely disable able WIFI?

---

### Post by SeijiSensei on 2015-03-20
My Brother color laser-class printer works fine with Linux.  You can also disable the wifi connection.  Mine is connected to my network via an Ethernet cable.  You have to choose one method or the other, though.

I'd never believe a salesman about anything having to do with Linux.  For printers, your best first stop is [http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/databaseintro](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/databaseintro).

---

### Post by whvw on 2015-03-20
Thanks for the tip on that website. It's the way to go. I can visit the site right in the store and get the straight story (at least on compatibility) on the spot. I'll check out Brother printers. Thanks again.

---

### Post by SeijiSensei on 2015-03-21
For reference, I'm using a [HL-3170CDW](http://www.amazon.com/gp/product/B00BQU141C/).

---

### Post by pdc on 2015-03-21
Goodness me: > The store salesman assured me that it would run under Linux. Well....it won't. .......... I would beg to differ................. and if I explain why below ..................

_____________________

.............if I go the US Canon site, and the MB2320 (Maxify) and click on linux drivers, I get to here [http://www.usa.canon.com/cusa/consumer/products/printers_multifunction/small_office_home_office_inkjet_printers/maxify_mb2320#DriversAndSoftware](http://www.usa.canon.com/cusa/consumer/products/printers_multifunction/small_office_home_office_inkjet_printers/maxify_mb2320#DriversAndSoftware)

and if I click on the Debian package, I click on that it downloads [COLOR="#008000"]cnijfilter2-5.00-1-deb.tar.gz[/COLOR] which is becoming the standard Canon download; it has an install script; whichever Canon printer you now buy; all of which will have 3 varieties of linux packages to support you; it will use this file...................anyone who wants to install the driver should click to download it; and select the **SAVE** option and it should then end up saved in their [COLOR="#0000FF"]Downloads[/COLOR] directory (also called folder)

_____________

to set up a printer; one seems to need to do 3 steps:

1) establish a connection 
2) install the drivers
3) register the printer on your computer (...ie so it knows what you are talking about ...)

__________

[SIZE=4]**1) establish a connection **[/SIZE]
so ............I am thinking whvw that you want to use a usb cable; (instead of wireless?): .............if so, I would suggest you just plug that cable in; as from here, [http://www.usa.canon.com/cusa/consumer/products/printers_multifunction/small_office_home_office_inkjet_printers/maxify_mb2320#Specifications](http://www.usa.canon.com/cusa/consumer/products/printers_multifunction/small_office_home_office_inkjet_printers/maxify_mb2320#Specifications) it has a high-speed usb port; 

____________-

[SIZE=4]**2) install the drivers and 3) register the printer on your computer **
[/SIZE]
The Canon install script does both 2) and 3) for you; whilst you watch the terminal; ...............so it will ask you if you wish for a wifi or usb connection; and you select which you want; the Canon install script does that for you; 

____________-

so I felt one should record here that the salesman was correct: Canon supply a debian package; tailor-built; that will install either a 32bit or 64bit driver; ..........and .............register the printer

_____________-

well; how to do all that stuff you ask?

1) if one opens a terminal and one way to do this is to hold the control and alt and t keys down at once .............

2) one needs to paste some commands into the terminal.............and whereas in most programmes the control and v keys do the paste command; the terminal is set up so you use three keys; the shift and control and v .......... if one practices a couple of times, it becomes easier; 

3) the commands below need to be copied; pasted into a terminal; and hit the ENTER key after each line is pasted; and have your sudo password ready; as you will be asked for it 

```
cd Downloads
```

```
tar -zxvf cnijfilter2-5.00-1-deb.tar.gz
```

```
cd cnijfilter2-5.00-1-deb
```

```
./install.sh
```

............that final command initiates the install script; 

________________________________________

> I'd never believe a salesman about anything having to do with Linux. .............well, maybe sometimes one should !

---

### Post by kerry_s on 2015-03-21
actually most work you just need to set it up as local driver & generic & postscript

i don't even bother installing drivers any more. i also have mine setup through google cloud print, so i can print anything from the browser.

---

### Post by SeijiSensei on 2015-03-22
I only buy printers if the drivers come with CUPS.  Relying on downloads from a manufacturer's site is discouraged on Linux systems for good reason.  Items in the repositories have been reviewed and tested by the developers and are known to work with the distributions with which they are shipped.  Having to download drivers from a manufacturer's site might be something Windows users do routinely but is something I use Linux to avoid.

---

### Post by Lori_Imel on 2015-03-22
I have tried several times to install my Epson 1430 printer via Printers in system settings....  but it would not work - it kept crashing.... So I went the CUPS route and it is working.... need to tweak the settings though - not doing what I want it to do .....

---

### Post by Mark_in_Hollywood on 2015-12-30
Discouraged? By whom? I cannot find documents about CUPS only printers and Linux.

---

### Post by SeijiSensei on 2015-12-31
The general rule of thumb for anyone other than experienced users is to rely on the repositories for everything.  As for printers and CUPS, see the link I posted earlier in this thread.  There isn't a "CUPS-only" printer, only printers for which Linux drivers exist that CUPS can use.

By the way, is there a reason you revived a nine-month-old thread?

---

### Post by Mark_in_Hollywood on 2016-01-13
In response to your question , this post made it possible for me to purchase (January 2016) the Canon Maxify MB2320 inkjet printer,  I didn't understand that the OP wanted a "cups only" printer. My sense was he couldn't get the right linux driver.

---

