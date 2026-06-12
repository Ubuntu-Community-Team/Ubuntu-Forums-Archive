---
title: "[SOLVED] Edgy and dell"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by squrl on 2006-12-10
6.1 edgy working fine. Dell 3110cn color laser not so fine.

This printer is on my LAN. It works going through the wife's windows box.

It doesn't work direct. Not good with wife's machine shut off. 

Printer is on port 192.168.15.102
Printer says it's name is DELL4106E8
MAC address is 08:00:37:41:06:e8
E net settings in printer say 10Base full
subnet 255.255.255.0
gateway addy 192.168.15.1

Status says ready
LPD port status enabled
Port status 9100 enabled
FTP port status enabled
SNMP port status enabled
E-Mail Alert port status enabled
EWS port status enabled
IP Filter Off

The driver is converted from factory supplied red hat
That converted driver is being used to print through the wife's XP machine

I have discovered you CAN NOT use the test page print. It is default to A4 paper and this printer won't accept that if there isn't A4 paper in the printer. The driver is both regular and PS. 

I have tried dozens of different setups and the printer just sleeps. I can print every time going through the wife's xp box.

Any help would be appreciated. 

Thanks

---

### Post by inacoma on 2006-12-16
I have the same problem.  When I was running Dapper with KDE it worked fine.  However, I created a fresh build with Edgy and have decided to use the Gnome desktop...now I can't get the printer to show up in the printers box.  I can go through the wizard setup just fine...but when done, I do not see the 3110cn as one of my available printers.

I travel for a living and have lots of printers installed with out problem..wonder why the dell and why now?

K

---

### Post by frost_ireland on 2007-01-09
I'm having the same problem, I've used alien to convert the 3110cn driver, then installed it.  I'm using Edgy with Gnome. Went through wizard no errors but then the printer doesn't appear!  Just bought this printer and got it working in XP in a few minutes, am dying to use it in a *real* operating system but am not sure where to go.  Anyone out there know what to try next?

---

### Post by npnutn on 2007-02-01
It appears I'm not alone.  My Dell 3110cn just arrived today, and after a few hours of messing around there is yet to be a printed page.  I'm using Edgy as well.  I even tried using the UXFILTER.tar instructions from the CD (it's intended for use on HP-UX, Solaris, and Linux).  Still no luck.

My symptoms are exactly as you all describe.  I'm hoping some beautiful person with all the answers will stumble upon this thread and fix all our woes.

I did just put a support request in with Dell.  I doubt they'll know how to proceed.  They are pretty M$ oriented.  

BTW, my wife dual boots between Ubuntu and Win98.  Win98 isn't supported either! :D  I don't know why that strikes me as funny.

---

### Post by npnutn on 2007-02-07
Well, Dell support is useless.  The Dell rep I "chatted" with couldn't even tell me where to find the ppd file for the 3110cn.  So I got it working on my own. :guitar: 

I set up an lpd queue in System -> Admin -> Printing, and used [this]("http://www.cups.org/strfiles/1985/color416.ppd") ppd file, from [this]("http://openprinting.org/show_printer.cgi?recnum=Dell-3110cn") page, but had no luck.

I also tried the alien rpm converter as described [here]("https://wiki.ubuntu.com/HardwareSupportComponentsPrintersDell") for Dapper (though I'm using Edgy).  Still no joy.

I finally tried the [ppd file]("http://www.cups.org/ppd/dell/en/dl3100cn.ppd.gz") for the 3100cn (not 3110cn) as found [here]("http://www.cups.org/ppd.php?L365+I0+T+QDell").  That one worked.  The crazy thing is, after that worked I reverted to the first driver and it worked too.  Weird.

It is printing to PostScript level 2, not 3, but I am sure this will eventually get worked out.  The color is great, and the printer is MUCH faster than our HP 2600n (which worked for about a year before the quality deteriorated beyond repair).

If you try to set up a 3100cn, do not use CUPS ipp protocol.  I get an error page when I do.

---

