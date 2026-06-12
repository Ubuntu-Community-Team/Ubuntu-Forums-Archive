---
title: "Can't get Canon MG5400 series Printer working in 14.04 LTS"
date: 2014-06-12
forum: Hardware
---

### Post by RandallSnyderJr on 2014-06-12
Hello,

I have purchased a Canon MG5422 multi-function scanner printer copier.  I have been able to prove the printer works fine in Windows and I can see the printer is recognized in Ubuntu as MG5400.  However, I have attempted 22 times so far to print a test page or other things with no luck.  I'm at a loss for what to do.  Any help will be most appreciated. :)

---

### Post by pdc on 2014-06-13
Hi Randall;

Canon provide a range of linux drivers for their Canon printers: if I guide you in how to install the 5400 series driver?

If you go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100467602.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100467602.html) and click the big red Download Now button; and if you elect to SAVE the package that is offered; the package will be [COLOR="#008000"]cnijfilter-mg5400series-3.80-1-deb.tar.gz[/COLOR] (and by default it should be saved into your Downloads folder);

You need to open a terminal: if that is new to you, click on the Dash or Search function on your desktop and type in terminal and it should appear..........to copy and paste, I suggest you use your mouse; and the top line of the terminal; ie File and along to Edit..and down to Paste

_________________________________________________

so plan is: copy each of the commands below that are in [COLOR="#FF0000"]**red**[/COLOR]; paste them sequentially into the terminal;)

(after pasting each command........make sure to hit the ENTER key to action your pasting)

_______________________________________________________

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -xzvf cnijfilter-mg5400series-3.80-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mg5400series-3.80-1-deb[/COLOR]

> [COLOR="#FF0000"]./install.sh[/COLOR]         ........that is going to run an install script; it will likely ask you for your sudo password; please have that ready; and you be asked if it is a usb or network connection;

.........it should all work and you should be able to print from eg LibreOffice

---

### Post by nick135 on 2014-08-12
I had the same problem printing from my Canon MG5450 networked printer. I found this Forum post, which helped, but there is one caveat I found with Ubuntu 14.04 - the initial driver install fails due to a dependency problem : 

[FONT=courier new]dpkg: dependency problems prevent configuration of cnijfilter-mg5400series:
 cnijfilter-mg5400series depends on libtiff4; however:
  Package libtiff4 is not installed.[/FONT]

Turns out that 14.04 has libtiff5 installed. I followed some advice on a similar forum thread here [http://ubuntuforums.org/showthread.php?t=2220935&highlight=canon+MG5400](http://ubuntuforums.org/showthread.php?t=2220935&highlight=canon+MG5400) and downloaded and installed libtiff4 package. [ Note that I used the official Canon drivers from the UK download site, which match yours, and not those on the post noted ]. After this I could successfully run the Canon driver install, which prompts for a few questions to connect to your printer...following that I can now successfully print to my networked Canon MG5450. 

Hope this helps.

---

### Post by sungstad on 2015-07-11
As Nick points out, this is a catch 22 situation. 
1. the pixma mg5400, mg5422 and  mg5400 cups drivers don't work. After the data is downloaded, it sits waiting to complete forever. Maybe a missing end of file?
2. the mg5400 version 3.80 driver did work before libtiff4 was replaced by libtiff5
3. libtiff4 is no longer available? I tried removing libtiff5 and it basically uninstalled the system (luxpuptahr).

I have an system that I  installed the mg5400-3.80 driver before it was upgraded to  libtiff5 and the driver still works, but I can not get anything to work on system that already have libtiff5.

Bottom line, can whoever maintains the cups drivers make a version that runs, and runs with libtiff5? Then we wouldn't have to go find patches like version 3.80?
BTW, cups before ~version 1.5 also have problems finding network printers and other problems. I know it's free but these problems have been around for some time, and now add up to a brick wall.

---

### Post by pwillman42 on 2015-10-17
I had the same problem with my MG5400 and this solved it for me, too.  Relatively new Ubuntu user (I'm on 14.04 LTS), and I was able to get this figured out no problem - thanks everyone!

---

