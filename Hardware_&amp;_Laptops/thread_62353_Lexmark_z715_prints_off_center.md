---
title: "Lexmark z715 prints off center"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by chowdah on 2005-09-04
I used the post here on installing the lexmark printer using the z600 driver and I got it working just fine, except that it prints off center.  Any text printed is moved about half an inch to the left.  It prints just fine except for this fact.  I tried looking at the configurations possible from the gui printer utility in ubuntu, but the only thing I could find was the print region selections, which didn't seem to have any effect.  Is there any way to manually change the print regions so that it is centered?

---

### Post by byourg on 2005-10-12
Download the drivers from this site:

[URL="http://users.cybercity.dk/~dko12479/"]http://users.cybercity.dk/~dko12479/
[/URL]
Get the files:
z700llpddk-2.0.1.i386.rpm
lexmark-z700-cups-driver-1.1.1-1.i586.rpm

Follow the steps in the Lexmark Printer Howto:

[http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark]("http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark")

These drivers fixed the off-center problem for me. I use a Z715 printer and tried the Z600 drivers but had the same problem as you. I installed these new drivers and it prints OK.

---

### Post by Chris Tucker on 2005-12-11
just a question, has anyone else had an issue with no space at the top of the page?
with the z600 driver, it was printing off center, but the space from the top of the page was fine, but with the z700 driver so far, no matter how many blank lines above the first line of text, it prints that first line RIGHT at the TOP of the page.. in most applications.

---

### Post by merlined on 2006-03-04
[QUOTE=byourg]Download the drivers from this site:

[URL="http://users.cybercity.dk/~dko12479/"]http://users.cybercity.dk/~dko12479/
[/URL]
Get the files:
z700llpddk-2.0.1.i386.rpm
lexmark-z700-cups-driver-1.1.1-1.i586.rpm

Follow the steps in the Lexmark Printer Howto:

[http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark]("http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark")

These drivers fixed the off-center problem for me. I use a Z715 printer and tried the Z600 drivers but had the same problem as you. I installed these new drivers and it prints OK.[/QUOTE]


This is another person trying to install the z715 printer. I am a complete newbie to Unix so I don't really know what I am doing. When I wen to the first link and clicked on "install z700llpddk-2.0.1.i386.rpm" then it tried to open it with the movie player and then it said it did not recoginize the stream or something like that. Even if that worked, I think I would have trouble doing the rest, let me know if you can offer me any help.
Kris

---

### Post by Dave54 on 2006-03-06
My printer is Z715.
Z600 driver: no left margin.
Z700 driver: no top margin.

For those who want to give it a shot, this is what I tried.
Myself; I'm gonna get a new printer.
Warning: I installed ubuntu yesterday as my first linux experience, so I haven't a clue what this code I made does.

1. download the files that byourg pointed out
2. make a folder on your desktop called "lexmark" (without quotation marks)
3. move the two files you downloaded into that folder
4. open "Terminal"
5. run the following commands:
```
cd ~/Desktop/lexmark
sudo alien -t lexmark-z700-cups-driver-1.1.1-1.i586.rpm
sudo alien -t z700llpddk-2.0-1.i386.rpm
sudo tar xvzf lexmark-z700-cups-driver-1.1.1.tgz -C /
sudo tar xvzf z700llpddk-2.0.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z700-lxz700cje-cups.ppd.gz
sudo /etc/rc2.d/S19cupsys restart
```

Again, I have no idea what this does and in the end it didn't work out for me.
If anyone notices something wrong with the code, please point it out.

---

### Post by Paul_M on 2006-11-12
I had the problem of pages printing off-centre with a Lexmark Z703 using Z600 drivers and read this thread to install the Z700 drivers, though when I came to remove then reinstall the printer it crashed the tool in KDE for this task, which no longer can display a list of printer drivers leaving me unable to install the printer until it is fixed, which is a pain

This has only happened on my laptop, I have yet to install the drivers on my desktop

Laptop is running a new install of edgy
Desktop is running Dapper

---

### Post by accludetuner on 2007-04-23
Ok guys, this is exactly what worked for me.  

The instructions in this Lexmark How-To did not work for me, but it is where I got  majority of the information. - [http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark](http://ubuntuforums.org/showthread.php?t=49714&highlight=lexmark)

I couldn't get it to print anything.  I would have been happy with it printing off-center like you guys are having issues with, but when I tried to print something it would just make a bunch of noise and suck the paper in and spit it out completely blank.  It was rather annoying.

I got a Lexmark z715 and both edgy & feisty and it now works great in both.

These instructions assume your USB is working correctly and that you already have "alien" installed from the package manager.  If this is not the case for you, search around because the instructions on how to take care of this is on the site.

go to a terminal and make a dir lexmark.  I made it in my home folder so that it was accessible regardless of which kernel I booted to.

```
mkdir /home/*YOURUSERNAME*/lexmark
```

As said above, download these files (right click, save as, and save them to your newly created lexmark directory):

[http://users.cybercity.dk/~dko12479/z700llpddk-2.0-1.i386.rpm](http://users.cybercity.dk/~dko12479/z700llpddk-2.0-1.i386.rpm)
&
[http://users.cybercity.dk/~dko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm](http://users.cybercity.dk/~dko12479/lexmark-z700-cups-driver-1.1.1-1.i586.rpm)


go back to the terminal and do the following commands:

```
cd /home/*YOURUSERNAME*/lexmark
sudo alien -t z700llpddk-2.0-1.i386.rpm
sudo alien -t lexmark-z700-cups-driver-1.1.1-1.i586.rpm
sudo tar xvzf  z700llpddk-2.0.tgz -C /
sudo tar xvzf lexmark-z700-cups-driver-1.1.1.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z700-lxz700cje-cups.ppd.gz
sudo /etc/init.d/cupsys restart
```

and just to check to make sure it being recognized properly:
```
cd /usr/lib/cups/backend
./z700
```

and it should show you this or something similar:
```
direct z700:/dev/usblp0 "Lexmark  Lexmark Z700-P700 Series" "Lexmark Printer"
```

If all is good, you can close the terminal out.

Go to SYSTEM > ADMINISTRATION > PRINTING to set up the printer
Select "New Printer"
Fill out whatever you want for Printer Name, Description, & Location
click "Forward"

Under "Select Connection" you should see "Lexmark Printer" and select that.
Next to it at "Enter Device URI" you should see the USB port where it is connected to ( such as - "z700:/dev/usblp0")
click "Forward"

You then have the option to "Select Printer From Database" or to "Provide PPD File".  Choose "Provide PPD File"
Select the location "/usr/share/cups/model/Lexmark-Z700-lxz700cje-cups.ppd"

When you're done and back at the main Printer Configuration page, you should see listed under Local Printers "Z700-v1.0-1".  That's a sign of success ;)  You can select it and change the options you want like making it your default printer, printing a test page, and so on, but that should pretty much do it.

I had tried many other ways and this was the only way that worked correctly for me.  I hope it can be of help to some of you other z715 owners.

---

### Post by gpilkay on 2007-07-10
Thank you so much for the help!  My Z715 FINALLY works!  Now to just get it to put space on the top of the paper...

---

### Post by sdowney717 on 2007-08-22
This got it working for me also, thanks.
I had some trouble getting it to show the "Z700-v1.0-1" printer created from the driver in the list. But a reboot and another cups restart and it was in the list.

---

