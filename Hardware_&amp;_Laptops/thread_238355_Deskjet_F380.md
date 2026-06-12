---
title: "Deskjet F380"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by l337dexter on 2006-08-17
So I have an HP Deskjet F380, and I am trying to install it via USB, but there is no actual F380 in the printers list.  Any suggestions?

---

### Post by zxee on 2006-08-17
Are you sure of that model#? It's not listed here [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi) either which is _the_
linux printer reference. If the model you've provided is correct chances are it's either not supported or you need to try a different but similar model driver and see if that will work.

---

### Post by l337dexter on 2006-08-18
I am 100% sure, I looked all over the box for any other label or identifying feature, the proof of purcahse even says HP Deskjet F380...

---

### Post by zxee on 2006-08-18
> **l337dexter said:**
> I am 100% sure, I looked all over the box for any other label or identifying feature, the proof of purcahse even says HP Deskjet F380...

There is an HP specific linux driver site here [http://hplip.sourceforge.net/supported_devices/index.html](http://hplip.sourceforge.net/supported_devices/index.html)
Your printer (which seems to be an all-in-one device?) is not on the supported devices list [http://hplip.sourceforge.net/supported_devices/combined.html](http://hplip.sourceforge.net/supported_devices/combined.html)

---

### Post by Gudanov on 2006-08-19
The F380 is on the supported list:

[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)

Hope it works! I have a relative I'm thinking about switching from Windows to Ubuntu if I can get the F380 connected to it to work. One month and the computer may need a reinstall of Windows to fix all the problems it is having with Internet usage.

---

### Post by tribaal on 2006-09-11
*bump*

Any news on how well the printer is supported? I'm looking into buying one of theses printers, but I would like to know how difficult it is to make it work...

Cheers

- trib'

---

### Post by franck.galbrun on 2006-09-18
I managed to get the F380 print under ubuntu dapper, using
System->Administration->Printers->add printer:

* There were 2 printers detected (!), "HP Deskjet F300 series" and "HP Deskjet_F300_series". It seems that it does not matter which one is chosen.

* As said in [http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html), F380 would work as a DJ3600 class printer, so I chose the "Deskjet 3650" driver.

That's all. Hope it helps.

My problem now is that I don't know how to get the scanner work. Any suggestion welcome !

Franck.

---

### Post by andrewski on 2006-09-21
> **franck.galbrun said:**
> * As said in [http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html), F380 would work as a DJ3600 class printer, so I chose the "Deskjet 3650" driver.

I see "DeskJet F300" in Edgy.  Just for the record....

---

### Post by Buzzygirl on 2006-09-22
Franck:

THANK YOU for your post! I received an F380 printer a few days ago as a birthday gift. I wondered which driver I should use to make it work with my Dapper machine. I tried a number of the listed drivers, but none of them worked, and as you know, there are dozens of driver possibilities between the two "detected" printers. The DJ3600 driver works, so you saved me hours of hunting for the correct driver! :D  

As far as getting the scanner to work-- not sure on that one. I don't really plan on using the scanner function of this printer anyway. Seems that one cannot buy just a simple PRINTER nowadays-- most of the printers sold in the stores around here are multi-function to some degree, and all I really need is a printer, not a scanner or fax machine too.

Thanks again!

---

### Post by Haegin on 2006-10-06
I have just got this working on Dapper using the Deskjet-3650 drivers. It printed a test page successfully but I cannot do more testing as I was only setting it up in the shop where I work.

---

### Post by tribaal on 2006-11-22
Just for the record: Apparently the scanner works out of the box with this printer.

Once the printer drivers are installed, just launch Xsane and start scanning... It's actually incredibly easy to scan stuff :) 

I love Ubuntu :)

- trib'

---

### Post by sawjew on 2006-12-03
> * There were 2 printers detected (!), "HP Deskjet F300 series" and "HP Deskjet_F300_series". It seems that it does not matter which one is chosen.


I have a Deskjet F380 which works perfectly under Dapper and Edgy but I will just point out to you that if you use the driver without the underscore in the name the HPLIP Toolbox will not recognise the printer.  I think you will find that the driver without the underscore is the hpijs driver whereas the one with underscores is the hplip driver.  They both use hpijs to print but the hpijs only driver does not use a graphical interface (hplip toolbox).

I actually downloaded the latest hplip self install package from their web site to use with Dapper and it worked perfectly.  I did have to install a couple of packages along the way but the installer tells you what you need. I am now using Edgy and the Deskjet F300 drivers are already installed.

---

### Post by StanMeis on 2006-12-11
Sawjew, when you say that you downloaded drivers for Dapper 6.06 that have an installer you referred to "their" website.  Who are the they that you're refering to, the Linux project or HP's website?  I bought an F380 for my wife and it's going to be under the tree on the 25th.  If I can install quickly I will be a hero, if I'm down in her office all morning muttering expletives I'll be a zero.  Any help, specifically a URL would be greatly appreciated.  As my signature says, I'm a rookie and need things to be spelled out.

Thank you.  :cool:

---

### Post by sawjew on 2006-12-11
> **StanMeis said:**
> Sawjew, when you say that you downloaded drivers for Dapper 6.06 that have an installer you referred to "their" website.  Who are the they that you're refering to, the Linux project or HP's website?  I bought an F380 for my wife and it's going to be under the tree on the 25th.  If I can install quickly I will be a hero, if I'm down in her office all morning muttering expletives I'll be a zero.  Any help, specifically a URL would be greatly appreciated.  As my signature says, I'm a rookie and need things to be spelled out.

Thank you.  :cool:

I was referring to the HPLIP website [http://hplip.sourceforge.net/]("http://hplip.sourceforge.net/")

The download URL for the HPLIP drivers is [http://hplip.sourceforge.net/downloads.html]("http://hplip.sourceforge.net/downloads.html")

If you download the self extracting archive with installer and then follow the directions on the download page it should install the drivers and, as long as your printer is plugged in and turned on when you do, it should automatically set up your printer for you.

Just make sure when you run the install command you use sudo to do it so your command should look like this ```
sudo sh ./hplip-1.6.10.run
```

The installer is supposed to automatically download and install dependencies through apt-get but it didn't work for me so **before you run the installer** open a terminal and enter ```
sudo apt-get build-dep hplip
```

This should take care of all your dependencies.

If you are running Edgy none of this is necessary you should be able to just plug your printer in and turn it on then go to >Administration>Printing and add New Printer.  The printer should be auto-detected so you can just select it and then just select HP Deskjet F300 series drivers.

After you have set up the printer all your features should be available under >Preferences>HPLIP Toolbox.

---

### Post by StanMeis on 2006-12-11
Thank you very much for the detailed instructions.  :)

---

### Post by shookone on 2006-12-12
I have the HP F380. It worked well under ubuntu dapper. Now for some reason, while in dapper, my HP DJ F380 decided to stop working. It will take in paper when you print but no print the first line or anything and just get stuck there. The power LED would start blinking.

I was having trouble with my machine anyways so i decided to format and install Edgy. Unfortunately i had no luck. I'm unable to get this printer to work again. It is as if linux capabilities broke. So I tried the printer on the WinBox and it worked with the drivers from HP.

I really wish i can trouble shoot this problem. I get some messages in my logs that i will post here as soon as i jump into linux.

---

### Post by fearpi on 2007-04-27
> **tribaal said:**
> Just for the record: Apparently the scanner works out of the box with this printer.

Once the printer drivers are installed, just launch Xsane and start scanning... It's actually incredibly easy to scan stuff :) 

I love Ubuntu :)

- trib'

It didn't work out of my box. How would I set up the scanner so that XSane recognizes it?

---

### Post by phstpok on 2007-05-10
Ubuntu 7.04

I bought an HP F380 and it installed with System>Printers>Add Printer. Printed well and copied but xsane would not recognise it. Came here and read earlier post about HPlip drivers, so downloaded hplip-1.7.4a.run and ran that. Didn't like it the first time, got error message about not being able to find the device (it was plugged in and turned on). I killed the install process and ran it again. This time it installed perfectly and printed out a colored test page. I used the test page to try scanning and xsane ran beautifully. My toolbox got installed in Applications>Accessories>HP Device Manager.

---

### Post by StanMeis on 2007-05-10
Sorry for not replying to everyone who has responded to my original post.  I'm running Ubuntu on my wife's PC and installed the HP Printer, Copier, Scanner over the holidays.  Her PC has been running flawlessly ever since whereas my XP box has required several trouble shooting sessions during that time.  Matter of fact, her computer is running so well that I rarely even look at it.  The printer install was done by following instructions in posts in this forum as well as on a Linux printer website.  The only problem has been trying to figure out where the low ink indicators are at.  Other than that all functions work great.

I'm in the process of trying to migrate my XP box to Ubuntu but have to resolve some issues.  I've got a $400 Epson printer that from what I have read is not well supported in Linux.  I've also got a Wacom tablet and a USB video capture device so that would be $600 of hardware that would not work at reduced capacity or not at all in Linux.  In addition I've got some Windows programs such as Noise Ninja with camera specific plug ins that I can't do without.  I tried Crossover Office and none of them worked so I put my complete switch to Linux on the back burner.  

Thanks for the response and good luck with the HP printers.  I'm a complete novice with Linux and got hers running with a minimum of troubleshooting.

---

### Post by nanamin on 2007-05-11
Installing the hplip package fixed it for me.

---

### Post by EL CHAVO on 2007-07-12
The Deskjet F380 worked fine for me. I added the printer (after verifiying I had hplip in synaptic) via the system panel and I can print, xsane in gimp recognized it right away! I did choose the driver with the underscore and that said hplip. I'm using Kubuntu, by the way.

---

### Post by alenburrows on 2007-09-29
Thanks for you help intall just as you said but if anyone knows how to get the scanner to work that would be a great help.
 Thanks

---

### Post by mjrclark on 2007-10-03
I too am considering buying this printer. The post two above me does claim to have the scanner working- no special configuration required. They have obtained pictures by going to  file->acquire->xsane in gimp. I guess just runnign xsane from the graphics menu would do the same.

---

### Post by OldGrey on 2007-10-15
Hi, 

I thought that I would add to this thread rather than starting another as I have a closely related issue. 

I use an F380 which works both as a printer and a scanner in Fiesty, no problems. However I have a concern about the print quality. The printer options only allows use of either the black or colour cartridge, not both at the same time. I have had a look around the HPLIP website and this seems to be correct. My concern is that if I go for colour the blacks are poor - washed out grey, but it is my only option if I want to print both text and pictures. I dual boot with XP and though it hurts to say it the XP drivers produce a far superior print. 

Am I missing something, is there a way to improve the print quality?

---

### Post by GepettoBR on 2008-04-08
Any news on how the F380 works under Gutsy? It's the last step towards getting my gf to switch from XP.

---

### Post by mjrclark on 2008-04-08
I have this printer and it worked fine- automatically detected, set-up etc. as far as I remember. Only problem was the low quality of OCR (probably a software thing though), other scanning and printing functions worked fine.

---

### Post by GepettoBR on 2008-04-08
Thanks a bundle!

---

### Post by StanMeis on 2008-04-08
> **mjrclark said:**
> I have this printer and it worked fine- automatically detected, set-up etc. as far as I remember. Only problem was the low quality of OCR (probably a software thing though), other scanning and printing functions worked fine.

Thanks for the reply but after running Ubuntu (with no problems) for a year on my wife's computer it was necessary to purchase a copy of XP.  My wife wasn't able to do a lot of things because she didn't have a windows or mac OS.  She was trying to install browser plugins for online discussion groups and that sort of thing.  In my case I would have lost the use of Namo web editor, Photoshop, Paint Shop Pro, Bryce 3d, as well as many other software titles.  It's not so much the cost of the software as the time it would take to find and learn alternatives.  My printer and USB video capture device were not supported either.  My wife is happy to finally be able to use the HP bundled software to monitor her ink levels.  Her games that she likes are now all working again and if she's happy I'm happy.

Ubuntu is a very stable OS and it would be great if I wanted to setup grandma for internet and email but if one is tied to a lot of graphics and web editing like I am the learning curve is too time consuming.  The Ubuntu forums were a great help and I used Linux for over a year so it was a good learning experiene.  I'm just too busy to work through these issues and can't afford to drop all the programs and hardware that isn't supported in Ubuntu.

---

