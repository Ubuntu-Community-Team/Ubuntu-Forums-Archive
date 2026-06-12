---
title: "Having trouble installing canon printer driver"
date: 2013-01-10
forum: Hardware
---

### Post by #1 fisherman on 2013-01-10
Hi I am Wondering if somone could help me with installing the driver for my canon pixma MG2120 printer. I found another thread that showed me where to download the driver but cant seem to get it up and running with the command posted in the thread. Everything seems great until I enter the install sh then I get error message 

An error occurred. The package management system cannot be identified.

I would really appreciate the help

---

### Post by pdc on 2013-01-11
welcome to the forum

the "why does this happen" is said to be

> [COLOR="Magenta"]It turns out that the script contains a serious oops that causes installs to fail if ANY [COLOR="Blue"]rpm[/COLOR] packages have been installed on the system[/COLOR]

you don't say if you have 32bit or 64bit: 

1) newbie to linux
2) canon printer

..........32bit is easier

**_[COLOR="Blue"]if 32bit[/COLOR]_** right click on the downloaded package; open with archive manager; open the directory or folder called packages; there should be 4: 2 common and 2 specific for the 2100 series printers;

1) right click on the common i386 and select install with gdebi installer

2) right click on the MG2120 i386 and select install with gdebi installer

.......should be good to go ....................

---

### Post by #1 fisherman on 2013-01-11
Thank you very much pdc Yes I am A noob. I got the printer printing in color by installing the deb packages like you said. I have yet to get the scanner to be detected tried doing the same procedure with the (scangearmp) deb packages without success. I would greatly appreciate it if you could reply with more awesome instructions. I have a 32 bit system

---

### Post by pdc on 2013-01-11
well done to get it all running! Enjoy! 

.......I learn new things every day; from a recent post I found a command

> [COLOR="Red"]cngpij P MG2100[/COLOR]

........try that........it should open up a GUI to help you set up things on your printer........

you can automate the launching of it...by creating a launcher..

try the instructions here:

[http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

if I summarise them ......

> [COLOR="Red"]sudo apt-get install gnome-panel[/COLOR]

then 

> [COLOR="Red"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]

then you should get something like the thumbnail I enclose below

[COLOR="Blue"]NAME:[/COLOR] can be whatever you want
[COLOR="Blue"]COMMAND:[/COLOR] cngpij P MG2100

......you can edit the image of the icon it creates when you feel like it

________________________________

now back to scangear

if you copy and paste

> [COLOR="Red"]sudo dpkg -l | grep scangear[/COLOR]

into a terminal........for my 3100 printer I see

> sudo dpkg -l | grep scangear
[sudo] password for pdc: 
ii  scangearmp-common                             1.80-1                                  ScanGear MP for Linux.
ii  scangearmp-mg3100series                       1.80-1                                  ScanGear MP for Linux.


..........so if you see that, ............(saying 2100!!) ..it is installed

if so, try copying and pasting

> [COLOR="Red"]scangearmp[/COLOR] into a terminal...........

........if that launches scangear, you create another launcher as above using the command 

> [COLOR="Red"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]

and then enter the details of name and command as needed

with NAME of whatever you wish and COMMAND as above ie scangearmp

---

### Post by #1 fisherman on 2013-01-11
RIGHT ON got it up and running in no time thanks to you pdc. I also got the launcher set up

---

### Post by pdc on 2013-01-11
great! enjoy!

---

