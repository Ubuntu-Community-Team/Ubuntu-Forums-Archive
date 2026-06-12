---
title: "Epson USB Printer Not Detected"
date: 2010-02-04
forum: Hardware
---

### Post by paulsp on 2010-02-04
Hi there,

I am trying to use an Epson receipt printer (TM-U220D) on Ubuntu. However, the printer is not detected when it is connected with a USB cable. After hours of searching I found other who had the same problem:

[http://forums.linux-foundation.org/read.php?36,7486](http://forums.linux-foundation.org/read.php?36,7486)
[http://ubuntuforums.org/showthread.php?t=1100608](http://ubuntuforums.org/showthread.php?t=1100608)

However, both solutions appear utterly complicated. Does anybody know a user-friendly solution? I also tried to simply add the printer and use "usb:/dev/usb/lp0" as Device URI. I then load the EPSONC drivers ([http://www.openprinting.org/show_driver.cgi?driver=epsonc&fromprinter=Epson-TM-U220D](http://www.openprinting.org/show_driver.cgi?driver=epsonc&fromprinter=Epson-TM-U220D)) but although it installs successfully, I am unable to print (no connection can be made, it says). 

Anybody knows a more or less user-friendly solution?

Thanks!
Paul

---

### Post by ellgor on 2010-02-05
Hi,

Take a look at the "Avasys" site, its for Epsosn's, their drivers are more up-todate.

Regards, Ellgor.

---

### Post by paulsp on 2010-02-05
Thanks Ellgor. However, these drivers appear to be for 'regular' printers only (see [http://avasys.jp/eng/linux_driver/download/](http://avasys.jp/eng/linux_driver/download/)), not for this receipt printer. I do not see any drivers for the TM series. Any other idea?

---

### Post by paulsp on 2010-04-09
Hello, 

I have been trying to install this printer for quite some time now, but I can not get it to work. Is there anybody who has any idea how to proceed? 

Printer Model: Epson TM-U220D (also known as M188D).

I connect the printer and it is recognized by lsusb:

> Bus 005 Device 003: ID 04b8:0202 Seiko Epson Corp. Receipt Printer M129C

When I go to CUPS it does not show up. Epson does not provide Linux drivers for this printer. At OpenPrinting this model is not listed and if I download the EpsonC drivers: 
[http://www.openprinting.org/driver/epsonc](http://www.openprinting.org/driver/epsonc)

Which are I think the closest I can get, then the printer is installed but when I try to print is says PRINTER NOT CONNECTED

My problem is the same as this thread:
[http://ubuntuforums.org/showthread.php?t=1100608](http://ubuntuforums.org/showthread.php?t=1100608)

But there is no solution there either.

I do not want to go back to Windows, but being able to use this printer is a requirement for me to work. Anybody any idea?!

Thanks!

---

### Post by ellgor on 2010-04-09
Hi,

I followed the link you gave in your last post which leads to here :

[http://sourceforge.net/projects/javax-usb/files/](http://sourceforge.net/projects/javax-usb/files/)

Now it doesn't give much in the way of how to go about things here, but if you click on the "support" tab, just above the green download box, this will take you to another page, click on the link for the  Project Homepage, you should now be at the Java page and click on the FAQ, from this list take a look at "Linux Implementation", its up to you if you want to continue, its actually straight forward following their guide??!

Regards, Ellgor.

---

### Post by paulsp on 2010-04-09
Hi Ellgor,

Thanks for your reply. You refer to this page? [http://javax-usb.org/faq.html#what_is_linux_imp](http://javax-usb.org/faq.html#what_is_linux_imp)

I read through the FAQ but I can not find instructions on how to install this. Maybe it's in there but it might be a bit too advanced. I am new to Ubuntu and if it does not say "apt-get install" or at least "unpack to this folder" then I easily get lost. Could you give a pointer?

Thanks!
Paul

---

### Post by WinterRain on 2010-04-09
Maybe you could run windows inside of virtualbox for printing, that way, you won't even have to reboot. This worked for me until I got a compatible printer.

---

### Post by paulsp on 2010-04-09
Thanks for the suggestion, but the printer is a fundamental part in a Point of Sales setup and receipts should be printed right away, without the need to switch to Windows...

---

### Post by paulsp on 2010-04-21
I have given up the idea of installing the printer in Ubuntu through CUPS. However, I was recently shown that it is also possible to use the "echo" command to print directly. Awesome!

This works very well:
echo "Testing" > /dev/usb/lp0

I thought this would solve my problems but it does not! I need to print output from a server to a printer connected to a client PC. So the (PHP) script that generates the information to be printed, can NOT be told to execute the "echo" command as the printer is not installed on the server. 

Anybody any idea how I can send this command to the printer on the client, directly from the server??

---

### Post by paulsp on 2010-04-22
Thanks for your reply. However, I do not really understand where to check and how. Could you elaborate a bit? Thanks!

---

### Post by hans-saarkham on 2010-11-01
Hi Paul,

maybe your problem has been solved. Otherwise:
I use an Epson TM-U220 on Linux Mint 9 KDE = Kubuntu 10.04.
POS software: Openbravo POS and the printer works.

No drivers needed and anyhow Espon drivers for Linux (CUPS & javaPOS) do not work for me.

First add the user who is using the POS to the lpadmin group via System Settings > User Management. 
Second printer configuration in O.B. POS: Printer = tmu-220, Mode = file, Port = /dev/usb/lp0. If you have more than 1 printer check which /dev/usb/lpx file is generated after switching on the printer.
Close and restart O.B. POS.

In this setting you are using ESC/POS to print directly to the Epson, but you need the privilege.

Note: this works only for the standard code page 0 (PC437) and code page 19 (international). If you want to print in other languages you will need to edit the source code to set the correct code page and add a translator file for Unicode to ASCII. 
This again only works foe languages which have a printer code page containing all characters of their language including accentuated and combined characters.
For some languages Epson refers to multi-strike font printing that will require more source code editing. 

Hans
Maha Sarakham, Thailand
------------------------------
Currently trying to implement 3-stroke Thai for Epson TM-U220M

---

### Post by paulsp on 2010-11-11
Thanks Hans. The problem was ultimately solved by printing with direct commands from the terminal, directly to /dev/usb/lp0. Not ideal but it works. Thanks in any way for your response!

---

### Post by hans-saarkham on 2010-11-15
Hi Paul,

not sure how you are using your TM-220D. I mean the application.
I use Openbravo POS software and want to print a receipt. O.B. is written in java. In O.B. I have to select the printer and it offers me several options. My printer is a TM-U220B and want to print Thai.
Being able to print from the command line indicates, you are part of the lpadmin group and that means have direct access to your printer.
O.B. printer configuration offers me several options, e.g. screen (can look on the screen to the receipt and it looks perfect). Printer where it is looking for  installed printers on the system. That means printers available through CUPS and you will need a printer driver. A pity, but there is no driver for Linux + TM-U220 that works on my system. I can print through my HP or to PDF. Other options are epson (general?) or tmu-220 (= epson) or star or ithaca. (other brands). In this case the application is addresses the printer directly (low level! = need to be member of the lpadmin group) using ESCPOS commands (THAT IS IMPORTANT). Other options like javapos and surepos require drivers and I cannot get working with Ubuntu 10.04.

Why several options for ESCPOS? BECAUSE NOT EVERY MODEL AND BRAND IMPLEMENTS ESCPOS IN THE SAME WAY.So depending on your application you may have to edit source code or just choose the correct configuration.

Let me describe what overcame me:
O.B. is claiming ESCPOS support for Epson TM-U220 with no driver installed and Thai localization. So I installed O.B. and it looked good. Next I bought an Epson TM-U200 supposed  to be supported. And  ...... it didn't work.
The issue here: it is not a serial but an USB connected printer.  So I had to add the user to the lpadmin group in Ubuntu and configure the printer in O.B, as Printer = tmu-220 / Mode = file / Port = /dev/usb/ lp1 (2nd USB printer on the system.
The printer printed rceipt, but .... no logo and .... no Thai.
O.B. offers to use a company logo (image file), but there seems to be an issue with the ESCPOS command for printing graphics.
My printer manual mentions that the Thai code page is default code page. But the printout for Thai characters was ????? (default setting in O.B.)
That meant I had to go into editing the source code of O.B.
First of all I had to change the selection of the code page selection.
Second of all. The java programming is based on UTF-8, no problem for Ubuntu, but for the printer. For this java offers a solution. In O.B. source code there are classes like UnicodeTranslator.java and UnicodeTranslatorInt.java taking care of translating Unicode UTF-8 to the printer codes. I had to create a UnicodeTranslatorThai.java file for Thai character conversion, a problem as the Thai code page replaces the 2nd half of the SCII table and needs addressing in &hex codes --> another conversion to find. Next I had to edit another file where printer settings for a.o. UnicodeTranslatorXXX.java are implemented to tell it to use UnicodeTranslatorThai.java class
Compile and he I can print Thai, but with limitations. 
Sofar it will print all languages where all characters including combined and accented characters are present in the printers code page.
BUT Epson is using a so-called 3-strike printing font for Thai. That means that combined fonts are actually printed using 3 lines of printing for one line in the receipt.
And there is where I am now, trying to program something I hardly understand in a programming language in my 1st encounter with it.

regards,

Hans

---

