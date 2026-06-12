---
title: "Lexmark x2600 series printer and Kde4"
date: 2009-04-11
forum: Hardware
---

### Post by Raptor Jesus on 2009-04-11
I recently updated to Kde4 and the lexmark driver I got from lexmark.com doesn't work anymore, It worked fine on Kde3. I get "cups-missing filter". Does anyone have any suggestions on what I can do to fix this?

When i run the konsole program i get this in console:

> Warning: Could not find '/usr/bin/adept_manager', starting '/bin/b Please check your profile settings.

---

### Post by HermanAB on 2009-04-11
Sell the Lexmark on Ebay and get an HP printer instead.

---

### Post by llamabr on 2009-04-11
> **HermanAB said:**
> Sell the Lexmark on Ebay and get an HP printer instead.

That's not very helpful advice.

Does it also not run in gnome?  How did you install the lexmark drivers?  Were they the redhat ones?  If so, you need to convert them with alien?

And what program are you trying to print from?

---

### Post by Raptor Jesus on 2009-04-11
I saved the archive from lexmark.com and ran the konsole program. I don't know about gnome, or alien. I don't think the driver was Red Hat. How can i go about finding out about gnome and alien?

Even with a HP printer it doesn't work. I go to the hplip site and download again, and I get this:

> Warning: Could not find '/usr/bin/adept_manager', starting '/bin/bash' instead.  Please check your profile settings. 

---

### Post by Raptor Jesus on 2009-04-12
Anyone can help me plz?

---

### Post by llamabr on 2009-04-12
Well, try it in gnome.  It may be the program you're using.  What program are you trying to print from.

When I set up my lexmark z600, I had to get, from lexmark.com, the linux driver which was a rpm, I believe.  You have to use alien to convert the rpm to deb, and then install.

So, where exactly do you find the driver?  And what instructions do you follow?

A quick search says that they have no plans to support that model:

[http://www.nabble.com/Lexmark-X2600-Series-td19988569.html](http://www.nabble.com/Lexmark-X2600-Series-td19988569.html)

---

### Post by Raptor Jesus on 2009-04-12
The problem is the

Warning: Could not find '/usr/bin/adept_manager', starting '/bin/b Please check your profile settings. 

I bet.


It does the same thing with a HP printer.

---

### Post by jbdavis52 on 2009-04-18
I am having a similar problem. I had a Lexmark X2600 driver and it even ran the maintenance stuff for the printer. But I had to reinstall Ubuntu due to an NVIDIA problem and lost it. Now I can go through the printer menu and can find where the program found my printer but there is no driver listed. I hate using "generic" because there are no controls in it for output.

---

### Post by jbdavis52 on 2009-04-25
> **jbdavis52 said:**
> I am having a similar problem. I had a Lexmark X2600 driver and it even ran the maintenance stuff for the printer. But I had to reinstall Ubuntu due to an NVIDIA problem and lost it. Now I can go through the printer menu and can find where the program found my printer but there is no driver listed. I hate using "generic" because there are no controls in it for output.
OK, I managed to solve this one. Listed in another post is the link to a 3rd party site that is an ftp download for the lexmark-inkjet-08 zip file that has the driver for the X2600. Also, if you go to [http://www.lexmark.com](http://www.lexmark.com) and select drivers and downloads from the pull-sown menu then select driver finder you will get to a page where you can choose your printer. Under 'select printer type' choose 'consumer inkjet printers' and then the z2300. There you will find a selection of OS's and if you click on Linux you will find a pulldown that lists all the major flavors including Ubuntu 8.04. That will open to a list of three files labeled lexmark-inkjet-08-1.0.1.i386.soforth...There is one for Kde. Just download, unzip and use terminal to install. You may need to use chmod +x to get it to work...This will make it a self installing archive. Works very pretty.

Once you do that, everything should be shiny.

John

---

### Post by JosephGarrison on 2010-01-24
> **jbdavis52 said:**
>   Just download, unzip and use terminal to install. You may need to use chmod +x to get it to work...This will make it a self installing archive. Works very pretty.

Once you do that, everything should be shiny.

John

I opened it in the terminal, but once it asks for my password and I enter it, it tells me it is incorrect. Did I do something wrong?

---

### Post by jflaker on 2010-01-24
I think the "sell it on eBay" advice was legitimate.  My new printer didn't work and I called Lexmark and they stated "They do not support Linux and do not plan to any time in the future."  I then asked if I just purchased a $90 paper weight and they said yes and that I should install Windows.

So, certain Brother and MOST HP printers are the better printers for cross platform support.

---

### Post by JosephGarrison on 2010-01-24
> **jflaker said:**
> I think the "sell it on eBay" advice was legitimate.  My new printer didn't work and I called Lexmark and they stated "They do not support Linux and do not plan to any time in the future."  I then asked if I just purchased a $90 paper weight and they said yes and that I should install Windows.

So, certain Brother and MOST HP printers are the better printers for cross platform support.

But there are drivers available for Linux, that customer service rep was just trying to get off the phone, otherwise he/she would have mentioned that and then gone through the proper steps for installation. People have gotten their printers to work, I'm still trying to figure it out though :(

---

### Post by jflaker on 2010-01-25
> **JosephGarrison said:**
> But there are drivers available for Linux, that customer service rep was just trying to get off the phone, otherwise he/she would have mentioned that and then gone through the proper steps for installation. People have gotten their printers to work, I'm still trying to figure it out though :(

Any ideas for a Lexmark X5070?

---

### Post by LowSky on 2010-01-25
[B][U]
[SIZE="5"]GUESS WHAT I FOUND THE DRIVER THAT WILL WORK IN UBUNTU for the X2600[/SIZE][/U][/B]
Please use the DEB package for Ubuntu for the X2600 link is below
[http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2600&actp=PRODUCT&id=DR860&segment=DOWNLOAD&userlocale=EN_US&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2600&actp=PRODUCT&id=DR860&segment=DOWNLOAD&userlocale=EN_US&locale=en)

> **jflaker said:**
> Any ideas for a Lexmark X5070?

Please do not post a questions about other printer, start your own so that other can find the thread and ask use t for help..
BY the way the X5070 is a paperweight according to this, sorry your out of LUCK!!
[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X5070](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X5070)

---

### Post by mjm1231 on 2010-01-26
Just by chance I was installing this model of printer tonight on my new install of Ubuntu 9.10, so I feel lucky a driver was found yesterday. The driver download from lexmark is a shell script. If you run it, you will be prompted for a password and it will fail. I suspect it is asking for the password for the root account, rather than for your own account to run sudo. To avoid this, launch the script using sudo instead:

"sudo ./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh"

Works nicely. Now all I have to do is figure out how to share it with the windows users in my house!

---

### Post by gunnut on 2010-05-13
Hate to resurrect an old thread, but I need some help with the same problem.

I am brand spanking new to linux, and I am trying to get my printer to work.
It is the Lexmark x2600. I found the right drivers for it, but when I start the install after accepting the terms and stuff it will not accept my password.

I have no clue what to do at this point, so please help....and I can't afford to get rid of the printer and buy another.

---

### Post by cloyd on 2010-05-13
There is an answer to the password problem. I had troubles with that on the x2600. For some reason, Lexmark wrote the driver so that it does not recognize Ubuntu's sudo accounts. You have to go to the terminal and establish a true root account, and establish a true root password. Give that password, and it will install.

I agree that "sell the Lexmark" is not helpful advice. But, though the printer is cheap, the color ink cartirdge is almost as much as the new printer . . . I bought a new HP that uses a $10 cartridge for each color . . . I think I'm gonna like it. But, since the x2600 does work with Linux, I am reluctant to pitch it.  My x5495 may be the one to get pitched.

---

### Post by gunnut on 2010-05-13
Okay, so there is light at the end of the tunnel now...but when I said I was "new" to Linux, I meant I am so new that I didn't even know it existed a few weeks ago.  I got so fed up with windows that I had to find an alternative. 

"You have to go to the terminal and establish a true root account, and establish a true root password. Give that password, and it will install."

I figured out what a terminal is, but I have no idea how to establish a true root account or password....I am willing to learn though :D

---

### Post by rf9rider on 2010-05-14
Easy way to install the Lexmark drivers.

Right click on the driver and select "extract here"

Then drag the extracted folder into your home folder.

You should then be able to set up/install your printer without passwords etc.

Worked for me with thanks to help on here.

---

### Post by gunnut on 2010-05-15
> **rf9rider said:**
> Easy way to install the Lexmark drivers.

Right click on the driver and select "extract here"

Then drag the extracted folder into your home folder.

You should then be able to set up/install your printer without passwords etc.

Worked for me with thanks to help on here.

I tried this and everything else I can think of right now with the same results.  It still is asking for a password and then not accepting it.

I realize I need to learn more about Ubuntu, but I really need my printer now.

---

### Post by Arkmow on 2010-11-05
I have a problem a little different. When I try to run the installer, I get a message that I should install cups 1.2 or higher.  No problem, but the version of cups I'm running is 1.4.3.  Anyone have this come up?
By the way I'm running Gnome

---

### Post by noobuntu9 on 2011-09-30
Hey all, I got my Lexmark x2650 installed and working! here's how...

download and extract this driver...

[http://support.lexmark.com/index?page=content&locale=EN&docLocale=en_US&segType=recommendedSegmentLINUX_UNIX&userlocale=EN_US&id=DR860](http://support.lexmark.com/index?page=content&locale=EN&docLocale=en_US&segType=recommendedSegmentLINUX_UNIX&userlocale=EN_US&id=DR860)

once extracted, copy the file (should be this file: lexmark-inkjet-08-driver-1.0-1.i386.deb.sh) and place it in your home directory. 

Open your terminal, and type in sudo -i to enable administrator privileges.

next, in the terminal once you have root privileges, type in: 

home/username/lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

(make sure you change "username" to YOUR account name)

That's it! Follow the installer and plug in the printer when prompted :)

It worked for me, I was not asked for a root password when I used this method.

---

