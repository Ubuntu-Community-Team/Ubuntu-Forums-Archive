---
title: "Laser toner HP Printer ?"
date: 2008-07-18
forum: General Help
---

### Post by pshah.mumbai on 2008-07-18
How do I set the darkness for the laser toner for b/w HP laser printer 1020

In windows I was able to set the darkness of the print. I cannot find any options in Ubuntu.

There is a option called brightness in printing options, but when I make it less than 100% it does the exact opposite and prints all the background as black (wasted a lot of tonner on this). It reduces the brightness of the background (makes it more dark) !!

Is there anyway I can reduce the darkness of the print for HP Laser printer ?

Atleast I was able to get the printer working by following the guide at

[http://www.linuxhaxor.net/2008/01/10/installing-hp-laserjet-1020-on-ubuntu/](http://www.linuxhaxor.net/2008/01/10/installing-hp-laserjet-1020-on-ubuntu/)

$ sudo apt-get install build-essential
$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
$ tar -zxvf foo2zjs.tar.gz
$ cd foo2zjs
$ sudo make uninstall
$ make
$ ./getweb 1020
$ sudo make install install-hotplug cups

After every restart, need to load the firmware by running the following command. The printer needs to be on while running the command or it gives an error.

$ sudo cat /usr/share/foo2zjs/firmware/sihp1020.dl > /dev/usb/lp0

You have to do the last step every time you want to print something.

---

### Post by ramjet_1953 on 2008-07-19
Do you have [COLOR="Blue"]hplip[/COLOR] and [COLOR="Blue"]python-qt3[/COLOR] installed?

If not, install them and use the command:

[COLOR="Red"]sudo hp-setup[/COLOR] to install the printer.

After this is done, you can use the [COLOR="Blue"]hp-toolbox[/COLOR] utility to do printer maintenance and alter settings

[COLOR="Red"]hp-toolbox[/COLOR]

Regards,
Roger :cool:

---

### Post by pshah.mumbai on 2008-07-19
thanks ! It detects the printer and works great :D

I still have this question, how do I reduce the darkness of the printouts and save on toner.

It has two options 

a. brightness 100% (default)
b. gamma 1000 (default)

I couldn't find any other options anywhere.

Reducing brightness will make the printouts with more dark background and not the text !

I windows printer settings there was a **slider that we can select the darkness level of the printouts. **I didnt find any such options in the HP Toolbox.

btw, thanks for pointing out to such a nice tool from HP :D

---

### Post by ramjet_1953 on 2008-07-20
Have you tried increasing the brightness?

i.e. Setting it to say 120%

Or increasing the gamma?

I can't really suggest anything else, as I use a HP inkjet, not a laserjet.

Regards,
Roger :cool:

---

