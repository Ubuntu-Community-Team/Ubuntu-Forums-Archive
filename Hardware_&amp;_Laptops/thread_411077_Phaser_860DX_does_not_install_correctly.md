---
title: "Phaser 860DX does not install correctly"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by tak1150 on 2007-04-16
Hi. I'm having a problem with installing Tektronix Phaser 860DX printer. The vendor provides a ppd file. I have tried:

System - Printing - Add Printer - IPP (it is on a network; it works with WinXP) - Tektronix - Phaser 850 (i figured it's the closest) - Choose the ppd file for the driver

Also through "localhost:631" I was able to install it as Phaser 860, but can never get it to print anything.

I know that the CUPS is working because I can print to another printer on the same network. Any help would be appreciated. Thanks.

---

### Post by tak1150 on 2007-04-24
Anyone? Help!

---

### Post by tak1150 on 2007-04-27
I figured out how to get the Phaser 860 printer to work. So I figured posting the how-to would benefit somebody :grin: 

prerequistes:
main administrator password/userid (if you're the only user, it's yours; otherwise the root's)
Phaser 860 DX PPD file you can get it [here]("http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=Z860&Xlang=en_US&Xcntry=USA&source=XOG&prodName=Phaser%20860").

Type the following in your web browser address bar
```
localhost:631
```

Should see something like this:
[ATTACH]31063[/ATTACH]

Click on Add Printer
Enter some info (name, location, etc)
When it comes to "device",
[ATTACH]31064[/ATTACH]

Select "AppSocket/HP JetDirect"
Click continue
Then for the address of the printer,
type
```
socket://111.111.111.111
```
Where 111.111.... is the IP address for the printer
Note if you chose IPP, it doesn't work.

Then when it asks you for the make & model,
just choose your PPD file that you downloaded earlier

Hope this works.

Blessings,
tak1150

---

### Post by jcrotteau on 2007-05-18
I followed all the advice here and couldn't get the printer to respond.

I then remembered that the Phaser 860 supports a number of protocols, some of which are turned off by default. I accessed the printer via its URL, went to the "Properties" section, then activated "Port 9100". After that, all went well.

Thanks to everyone for the previous advice.

---

### Post by sacherjj on 2007-06-23
Installed my Xerox Phaser 8500 without any problems.  The PPD files I downloaded from Xerox site (for all possible printers) were in a .exe.  Turned out to be a WinZip executable.  Run in WINE allowed me to extract them with no problem and I just printed my test page.  

Thanks for the thread, exactly what I needed.  I'll get this Ubuntu thing figured out yet.

---

