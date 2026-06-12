---
title: "printer installation help - lexmark x1150"
date: 2007-03-23
forum: Hardware &amp; Laptops
---

### Post by chicki on 2007-03-23
Hello!

I'm having a problem getting my new printer to work with Kubuntu. I'm new to Linux, so I'm still a little confused. It is a Lexmark x1150, and I really would like some instructions.

Thanks!

---

### Post by ramjet_1953 on 2007-03-24
Hi, there!

It probably would have been prudent for you to have done a little more research, before buying a Lexmark printer for use with Linux. Lexmark are probably the least Linux friendly printers out there and they don't offer any open source drivers.

Even Turboprint don't support Lexmark!

However, if you go to this site [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi) , you will see that the X1150 is not listed, but the X1100, X1130 and the X1170 are listed.

You could try the listed suggestions and see if you have any joy.

Regards,
Roger 8)

---

### Post by jclbx on 2008-03-04
installation Lexmark x1150 sous kubuntu 7.10

j'ai lancé Adept Manager et installer le package : z600cups.

puis 

après avoir téléchargé le package : z600llpddk_2.0-2_i386.deb


 sudo dpkg -i z600llpddk_2.0-2_i386.deb   

Et la miracle mon imprimante imprime en couleur

Notes : 
	je ne désire à ce jour que le module imprimante, plus tard je regarderais pour le scanner

:guitar:Merci a vous tous pour vos infos.
:lolflag:

---

### Post by chicki on 2008-03-26
> **ramjet_1953 said:**
> 
It probably would have been prudent for you to have done a little more research before buying a Lexmark printer for use with Linux. 



Actually, I did not buy this printer. It was a hand-me-down from my parents. It seems like a new printer to me though. 


> **ramjet_1953 said:**
> 
Lexmark are probably the least Linux friendly printers out there and they don't offer any open source drivers.

Even Turboprint don't support Lexmark!



Thank you for the info. I'll keep that in mind when I buy myself a printer. 


> **ramjet_1953 said:**
> 
However, if you go to this site [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi) , you will see that the X1150 is not listed, but the X1100, X1130 and the X1170 are listed.



Actually X1150 is listed. It is listed as x1150 PrintTrio. (That's the printer that I have.)


----------------------------------------------

(OpenPrinting database - All Lexmark Printers)
[http://www.linuxprinting.org/printer_list.cgi?make=Lexmark](http://www.linuxprinting.org/printer_list.cgi?make=Lexmark)

The URL above shows that my Lexmark x1150 PrintTrio printer should work perfectly with Linux (three penguins).


----------------------------------------------

(OpenPrinting database - Printer: Lexmark x1150 PrintTrio)
[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x1150_PrintTrio](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x1150_PrintTrio)

The URL above recommends to install this driver: CJLZ600LE

Note: This driver works on most models of Lexmark.

--------------------------------------------

Thanks for your help. That URL gave me some hope that I can print in Linux and not use Windows to print. 

~chicki

---

### Post by chicki on 2008-03-26
> **jclbx said:**
> installation Lexmark x1150 sous kubuntu 7.10

j'ai lancé Adept Manager et installer le package : z600cups.

puis 

après avoir téléchargé le package : z600llpddk_2.0-2_i386.deb


 sudo dpkg -i z600llpddk_2.0-2_i386.deb   

Et la miracle mon imprimante imprime en couleur

Notes : 
	je ne désire à ce jour que le module imprimante, plus tard je regarderais pour le scanner

:guitar:Merci a vous tous pour vos infos.
:lolflag:


I am not sure what you typed because it is in french, but thanks for your help though.

~chicki

---

### Post by oldsoundguy on 2008-03-26
just remember you are trying to use the Yugo of printers.  Don't expect miracles.

---

### Post by chicki on 2008-03-26
Here is an update:

It's been a year now and I finally got my Lexmark x1150 printer to print in Ubuntu 7.10 Hooray!

Note: I use Ubuntu now, not Kubuntu. The printer should work in both though.


----------------------------------

The URLs below are step-by-step instructions on how to install the z600 driver which works on most models of Lexmark. 


---------------------------------

(Installing the Z600 Driver) (aka CJLZ600LE driver)
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)

The URL above shows step-by-step instructions on how to install the Z600 driver. 
Follow the instructions.
Ignore the URL in step 3. (It was confusing. I think it's for gentoo users.)
You will need sudo in front of alien ...
You will probably need to install alien (apt-get install alien)

Note: If the z600 file did not output anything, then go to the link below.


----------------------------------

(HOWTO: Lexmark Printers)
[http://ubuntuforums.org/showthread.php?t=49714&highlight=X1150](http://ubuntuforums.org/showthread.php?t=49714&highlight=X1150)

The URL above is the same thing with a little more instructions at the end.  
The z600 file did not output anything. So I followed the instructions in the URL above.

Note: The URL above forgot to install the following package:
         
         sudo apt-get install libstdc++5 alien

Make sure you install that package by copy-pasting the line above.


----------------------------------

So after all that, my Lexmark x1150 PrintTrio seems to work.

However, it is printing blank pages. I think I am out of ink. 

After I get ink, I'll give an update whether or not this printer prints in color or only in black and white or still in blank pages.

----------------------------------

I hope this helps others and Thanks to everyone who replied.

~chicki

---

### Post by simonvdavis on 2008-04-15
hi ! there i also have a lexmark x1150 trio. That i am having real problems with.Did you have much success with your printer ? If so i would be very interested in how you did it 


                                            thank you simon

---

