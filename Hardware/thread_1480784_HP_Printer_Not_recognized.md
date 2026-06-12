---
title: "HP Printer Not recognized"
date: 2010-05-11
forum: Hardware
---

### Post by breimer273 on 2010-05-11
So I have this HP Printer and it is not being recognized as a printer that I can print to. I tried downloading the HPLIB from HP's website but I could have done that wrong. The printer was on the list of supported printers, its a deskjet all in one. Don't remember the number off the top of my head but I can look it up when I get back if someone really needs me to. Thanks in advance again.

---

### Post by breimer273 on 2010-05-12
I just wanted to bump and add that it is a HP F4280 all-in-one printer.

---

### Post by vinnie1 on 2010-05-12
Hi

According to my research this printer should work without any hassles.

Things to try - 

1. from console try **lsusb** -  You should see the printer listed.

If not then you have a hardware problem, (try a different usb port)

If it is listed then try **hp-setup** from the console.


Let me know what happens and I'll try and help


P.S what version of Ubuntu are you using  ??

---

### Post by breimer273 on 2010-05-13
> **vinnie1 said:**
> Hi

According to my research this printer should work without any hassles.

Things to try - 

1. from console try **lsusb** -  You should see the printer listed.

If not then you have a hardware problem, (try a different usb port)

If it is listed then try **hp-setup** from the console.


Let me know what happens and I'll try and help


P.S what version of Ubuntu are you using  ??

OK first I am using Lucid (10.04) I went to hplipopensource.com and used the installer there. When I run the commands in terminal this is the output:
> 
bill@bill-laptop:~$ lsusb
Bus 004 Device 003: ID 05ac:8213 Apple, Inc. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05ac:0236 Apple, Inc. 
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 031: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 030: ID 059b:0277 Iomega Corp. 
Bus 002 Device 029: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 002 Device 003: ID 05ac:8403 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 017: ID 03f0:2504 Hewlett-Packard 
Bus 001 Device 004: ID 05ac:8507 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bill@bill-laptop:~$ hp-setup

HP Linux Imaging and Printing System (ver. 3.10.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
/error: No PPD found for model deskjet_f4200_series using new algorithm. Trying old algorithm...
error: No PPD found for model deskjet_f4200 using old algorithm.
error: No appropriate print PPD file found for model deskjet_f4200_series



I know that it is SUPPOSED to work out of the box but this isn't thus why I am posting on the forums trying to get an answer.
Thanks for the help,
Bill

---

### Post by vinnie1 on 2010-05-13
Hi

As an example this is what I get when I plug in my HP Deskjet F2180 All in one

> 
vincent@acer1:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 03f0:7d04 Hewlett-Packard DeskJet F2100 Printer series
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


You can see it is clearly labeled.

I see from your listing that you have a lot of stuff plugged in.

I would try, in the following order

1. Unplug every other usb device and see if the printer gets listed with **lsusb**, also try different usb ports.
2. Re-install Ubuntu. I suggest this because when I run the command **hp-setup** I get a GUI screen pop up.

Let me know how you get along.

---

### Post by breimer273 on 2010-05-14
I do get the gui screen pop up when I run hp-setup but I get the same no matching PPD file error. Maybe I can just get a PPD file for this from somewhere?

---

### Post by vinnie1 on 2010-05-14
Have you seen this website

[http://hplipopensource.com/hplip-web/install/install/index.html]("http://hplipopensource.com/hplip-web/install/install/index.html")

Did everything happen as it says.

Have you tried different usb ports, etc. Also try the live CD again.

Not sure what more to suggest.

---

### Post by stuart.reinke on 2010-07-20
> **breimer273 said:**
> So I have this HP Printer and it is not being recognized as a printer that I can print to. I tried downloading the HPLIB from HP's website but I could have done that wrong. The printer was on the list of supported printers, its a deskjet all in one. Don't remember the number off the top of my head but I can look it up when I get back if someone really needs me to. Thanks in advance again.

Did you get your printer to work? I have the same printer and had the same exact problem and error messages.

My problem showed up after switching to Ubuntu 10.04 from openSUSE 11.2. I kept the same /home partition and I think there were some left over config files mucking things up.

A reinstall and new /home partition fixed my problem.

---

### Post by businessanalyst on 2010-07-20
I had a very similar  problem and it was simple to fix. Lie to your computer. Tell it you have a another printer - preferably an older simpler one in the same line.

---

### Post by swiftwood on 2010-07-20
> **vinnie1 said:**
> Have you seen this website

[http://hplipopensource.com/hplip-web/install/install/index.html]("http://hplipopensource.com/hplip-web/install/install/index.html")

Did everything happen as it says.

Have you tried different usb ports, etc. Also try the live CD again.

Not sure what more to suggest.


Just thought I'd give this a bump

I bought an HP 4500 today

When I tried autoconfigure it, it started printig out page after page.

Your tip saved the day. Worked like a charm!

thanks!

---

### Post by VitaLiNux on 2010-07-20
I found that quite odd since HP does give a good driver support through [**HPLIP**]("http://www.google.com/url?sa=t&source=web&cd=6&ved=0CDIQFjAF&url=http%3A%2F%2Fwww.openprinting.org%2Fdriver%2Fhplip&ei=kFhGTNf0CYH88Ab-6LziBA&usg=AFQjCNEN01vOWGWox5GGBQ-0MisGTZSe7A"). :-k

---

### Post by ReDRMo on 2010-07-24
I downloaded HPLIP-3.10.6.run, but when I try to install it (sh hplip-3.10.4.run) it doesn't work...

---

