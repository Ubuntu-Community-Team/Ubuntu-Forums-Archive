---
title: "Lexmark x7675 drivers"
date: 2010-03-10
forum: Hardware
---

### Post by Fattymac on 2010-03-10
I have recently come over to UBUNTU and I already owned a Lexmark x7675 all in one printer.  I know that this printer is not compatible with Ubuntu (somehow) and that Lexmark have not released the drivers for this.

I have written to Lexmark and they have not replied to my request to make Ubuntu drivers available to me.

I was wondering:

1. Has anyone actually got this printer to work on Ubuntu.  I have tried many ways including ndiskgtk and the driverloader.  None work

2. Surely the code programmers at Ubuntu can make this printer compatible without waiting for the drivers to be released from Lexmark.  We all know Lexmark are behind the times when running linux but come on....  someone can make an all in one printer work on linux, surely otherwise what is the point??

I love Ubuntu and have only had it for a week but someone out there has surely got a solution to this problem....

---

### Post by larrys4227 on 2010-03-10
Just released on 3/4/2010 ......  give it a shot.  Worked great for me!

[http://support.lexmark.com/index?page=content&locale=en&productCode=LEXMARK_X4650&segment=DOWNLOAD&oslocale=en_US&actp=CONTENT&userlocale=EN_US+&id=DR20523](http://support.lexmark.com/index?page=content&locale=en&productCode=LEXMARK_X4650&segment=DOWNLOAD&oslocale=en_US&actp=CONTENT&userlocale=EN_US+&id=DR20523)

---

### Post by Fattymac on 2010-03-10
After I vented my anger in my last post :) i received an email from Lexmark telling me that they had their new driver for this system which is named lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz
 
I am away for a bit but I will check it when I get home.
 
Did you have any dramas installing it? Did you just execute the sh file?
 
Thanks for the reply.
 
If this works, I will be a happy man.
 
[_[SIZE=2][COLOR=#0000ff][SIZE=2][COLOR=#0000ff]http://support.lexmark.com/index?locale=en&productCode=LEXMARK_X7675&userlocale=EN_US&segment=DOWNLOAD&os=UBUNTU_9.10&page=downloadsList&oslocale=en_US#1[/COLOR][/SIZE][/COLOR][/SIZE]_]("http://support.lexmark.com/index?locale=en&productCode=LEXMARK_X7675&userlocale=EN_US&segment=DOWNLOAD&os=UBUNTU_9.10&page=downloadsList&oslocale=en_US")

---

### Post by PTelly on 2010-04-14
I have tried to execute this driver several times (even re downloaded several times) Each time I try to install I get to the point where it ask for password and each time "it" informs me that I have entered the wrong pw! Lexmark support is not of any help. Hopefully someone can guide me through this so I do not have to boot into ...dows each time I want to use printer.Any thought/help will be greatly appreciated.
Ubuntu 9.10
Thanx

---

### Post by Fattymac on 2010-05-03
I just reinstalled my drivers.  I had the same password issue to start with so i just exeuted the file using sudo and it worked no problemo!

---

### Post by randywebdesign on 2010-05-31
> **Fattymac said:**
> I just reinstalled my drivers.  I had the same password issue to start with so i just exeuted the file using sudo and it worked no problemo!

Can you please provide the steps for a newbie in terminal that you did to get the .deb.sh.tar.gz file form lexmark to install.

---

### Post by korn101 on 2010-11-01
> **randywebdesign said:**
> Can you please provide the steps for a newbie in terminal that you did to get the .deb.sh.tar.gz file form lexmark to install.

Right Click the Archive ---> Extract Here

It should extract it to a file called lexmark-08z-series-driver-1.0-1.i386.deb.sh

Copy this file to your desktop.

Then, open up Terminal ( Applications -> Accessories -> Terminal )

type "cd Desktop" (without quotation marks)

it should change the current directory to the Desktop ( Should look something like this: jaime@jaime-laptop-linux:~/Desktop$ )

Then type "./lexmark-08z-series-driver-1.0-1.i386.deb.sh"

Then follow the setup prompt that follows. 

If you get the password error then:

instead of typing "./lexmark-08z-series-driver-1.0-1.i386.deb.sh"

try typing "sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh" or "sudo lexmark-08z-series-driver-1.0-1.i386.deb.sh"

The terminal will prompt you for your password, enter it.

Then it should start and work perfectly fine :)

Hope I helped, although I am a bit late :/

---

### Post by dabomb1022 on 2010-11-27
thanks, for the help. I got it installed but now it says to plug in the usb cable. I can't because my nettop is too far away. Anyway around this? It is wireless after all.

---

### Post by dabomb1022 on 2010-11-27
I figured it out! Once you get to the page asking to plug in your printer you can cancel and leave the installation. Then go to your router, mine is 192.168.1.1 and find your printer ip address. Then you open up printers under administration and put in the ip address of the printer and let it print a test page! See mine here: 
[IMG]http://desmond.yfrog.com/Himg13/scaled.php?tn=0&server=13&filename=ez7m.jpg&xsize=640&ysize=640[/IMG]

---

### Post by hackman17 on 2010-11-28
Hey does anyone know if these drivers or some other drivers will work with powerbook g4/powerpc running ubuntu??

---

