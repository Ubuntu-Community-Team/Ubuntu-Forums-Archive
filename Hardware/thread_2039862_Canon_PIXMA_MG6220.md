---
title: "Canon PIXMA MG6220"
date: 2012-08-09
forum: Hardware
---

### Post by malelecol on 2012-08-09
Hi, I need HELP. I bought a Canon multi functional printer and I have not been able to make the scanner work yet. The printer works fine. I downloaded the drivers for the MG6200 and still not working. Also installed XSane and still not successful. Please help. Thanks

---

### Post by llmunro on 2012-08-09
Well, hi!

I don't have this exact model of Canon PIXMA printer/scanner/copier, but I have the Canon PIXMA MX860.  I have successfully gotten it to work ever since Ubuntu 11.10 without too many problems.  I believe you need to download the correct Linux drivers for your PIXMA from the Canon Europe site-- I seem to recall that they come as .deb files and it isn't hard to install them.  I think there's two of them.  (One is called scangear, if I recall correctly.)

You might also find some help in this very long thread of mine a while back in which I try to get the PIXMA scanner working.

[http://ubuntuforums.org/showthread.php?t=1463237](http://ubuntuforums.org/showthread.php?t=1463237)

Although I've gotten Canon PIXMAs to work with Ubuntu, I've had way better luck with HP printer/scanner/copiers, just for future reference.

Hope that helps.
Best,
Lisa

---

### Post by malelecol on 2012-08-09
Hi Lisa,I read all your thread and did some things suggested there but still no luck. I think I am giving up. Thanks

---

### Post by jmcdougall on 2012-10-11
I just bought the Canon MG6220 all in one printer and got the scanner working on Ubuntu 12.04.  Here is how it is done.

Download the scanner software from this page:
[http://support-sg.canon-asia.com/contents/SG/EN/0100396002.html](http://support-sg.canon-asia.com/contents/SG/EN/0100396002.html)

Extract the archive into a folder of your choice.  It will put all the files in a folder something like: 
scangearmp-mg6200series-1.80-1-deb

Open a terminal and cd to that directory.

Inside that directory, you will find a file called "install.sh".
Run it by typing:
./install.sh

It will ask for a password and install the packages.

Here is where I had a problem.  I had a hard time finding what was supposed to be run to use the scanner.  At a terminal, type:

scangearmp

That will open up the scan gui for the printer.

You can create an entry that Unity will recognize in the dash with a program called:
"Create Launcher" that can be found in the Ubuntu Software Center.  The program is free, but you must press the "buy" button for the price of $0.00 and log into ubuntu to complete the "free" purchase.

I hope this helps.
John

---

### Post by michael37 on 2013-02-04
> **jmcdougall said:**
> I just bought the Canon MG6220 all in one printer and got the scanner working on Ubuntu 12.04.  Here is how it is done.

Download the scanner software from this page:
[http://support-sg.canon-asia.com/contents/SG/EN/0100396002.html](http://support-sg.canon-asia.com/contents/SG/EN/0100396002.html)

Extract the archive into a folder of your choice.  It will put all the files in a folder something like: 
scangearmp-mg6200series-1.80-1-deb

Open a terminal and cd to that directory.

Inside that directory, you will find a file called "install.sh".
Run it by typing:
./install.sh

It will ask for a password and install the packages.

Here is where I had a problem.  I had a hard time finding what was supposed to be run to use the scanner.  At a terminal, type:

scangearmp

That will open up the scan gui for the printer.

You can create an entry that Unity will recognize in the dash with a program called:
"Create Launcher" that can be found in the Ubuntu Software Center.  The program is free, but you must press the "buy" button for the price of $0.00 and log into ubuntu to complete the "free" purchase.

I hope this helps.
John

John, the instructions are awesome. Worked for me on Ubuntu 12.04 64-bit perfectly.

Do you know if there is any way of making this scanner work with sane (and therefore work from within gimp)?

---

### Post by jmcdougall on 2013-08-31
> **michael37 said:**
> John, the instructions are awesome. Worked for me on Ubuntu 12.04 64-bit perfectly.

Do you know if there is any way of making this scanner work with sane (and therefore work from within gimp)?

I have looked hard and have found no way to get sane to recognize the Canon PIXMA MG6220.  I should have had some forethought when I purchased the scanner and looked for a compatible one.

---

### Post by michael37 on 2013-09-02
> **jmcdougall said:**
> I have looked hard and have found no way to get sane to recognize the Canon PIXMA MG6220.  I should have had some forethought when I purchased the scanner and looked for a compatible one.

Thanks, I've been researching this myself and came to the same conclusion.

---

### Post by pdc on 2013-09-03
ScanGearMP creates a menu entry within GIMP:

> (and therefore work from within gimp)?

Open GiMP:

Go to:

File

Create ......ScanGearMP .....................

---

