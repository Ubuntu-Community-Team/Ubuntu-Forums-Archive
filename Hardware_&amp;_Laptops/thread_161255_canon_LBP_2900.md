---
title: "canon LBP 2900"
date: 2006-04-16
forum: Hardware &amp; Laptops
---

### Post by cosimo.it on 2006-04-16
Hi everyone!
I'm new in the world of linux and ubuntu.
I've got a problem with configuring my laser printer canon LBP2900.
I've already found the drivers at the canon web-site (they say they tested them on a RedHat and on SuSE). When I try to register the printer (PPD) with the spooler by means of the command:

	# /usr/sbin/lpadmin -p [printer name] -m [PPD file name] -v ccp:/var/ccpd/fifo0 -E

I receive the answer:

	lpadmin: add-printer (set device) failed: client-error-not-possible

Is there someone who can give me some help?
Cosimo

---

### Post by Sef on 2006-04-23
Did you use alien to convert the files to .deb?

---

### Post by krokodil on 2006-06-02
My parents recently got this printer too, and I'm struggling to get it installed. I converted the rpm from Canon with Alien and installed the deb.

I can see the driver files when I try to setup the printer through Gnome but I can't seem to get it to print.

If I set it up as a local printer it says it's printing but nothing happens. If I set it up using the lpadmin command I get an error, but the printer is registered. However when I try to print it fails and asks whether the printer is switched on (it is).

As far as I understand you need to run ccpd, and register the printer on there, which I've done.

Perhaps you have to run the printer as a networked printer so it can talk to ccpd?

Can't find any help anywhere. Will be upgrading to Dapper soon but I have a feeling that won't fix the problem.

-Rudolf

---

### Post by blair on 2006-06-03
Make sure the PPD file is in /usr/share/cups/model directory - NOT one of the subdirectories under there. CUPS may choke if the PPD file is somewhere else. Then try your setup and again annd restart cupsys.

---

### Post by krokodil on 2006-06-15
Sorry for the long time between replies, I only get to work on this computer (the one with the printer attached) about once a week.

The PPD files are in the correct folder.

---

### Post by krokodil on 2006-08-08
**I FINALLY got my Canon LBP 2900 printer to work on Dapper** thanks to kindly being directed to *another* French wiki article on how to install the Canon LBP 2900 on Kubuntu Dapper.

As mentioned the article is in French but if you just follow the commands, step by step - as I did, I can't read French - and occasionally refer to a Google translation you should do fine.

**Important! A few things I picked up from the Google translation:**

Etape 8 (Step 8?) says to switch off the printer and then to reboot. After you've logged in turn on the printer again.

Etape 9 describes tests to check that your printer has been installed correctly.

Don't trust the Google translation as far as commandline things go, it massacres the formatting.

If you can't make sense of the French article, I intend to rewrite the article in English and post it on the wiki soon.

Based on the drivers provided I assume this will also work for the Canon LBP 1120, 1210, 3000, 3200, 3210, 3300, 3600, and 5000 printers.

Original:
[http://doc.ubuntu-fr.org/materiel/imprimante_canon_lbp_2900](http://doc.ubuntu-fr.org/materiel/imprimante_canon_lbp_2900)

Google Translation:
[http://translate.google.com/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fmateriel%2Fimprimante_canon_lbp_2900&langpair=fr%7Cen&hl=en&ie=UTF8](http://translate.google.com/translate?u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fmateriel%2Fimprimante_canon_lbp_2900&langpair=fr%7Cen&hl=en&ie=UTF8)

---

### Post by krokodil on 2006-08-14
I have completed the translation, it can be found here:

[https://wiki.ubuntu.com/Canon_LBP_2900_HowTo](https://wiki.ubuntu.com/Canon_LBP_2900_HowTo)

---

### Post by PPisHere on 2006-08-28
Hi,

I am desperate, I followed the install guide from top to bottom. But no lack. My Canon is dead.

finally I checked [www.linuxprinting.org]("http://www.linuxprinting.org") and there was a solution, 'Do not use Canon' :) so have anybody has idea how ro proceed with Canon or should I go back to shop and change it to e.g. Epson or HP?

---

### Post by PPisHere on 2006-08-28
> **PPisHere said:**
> Hi,

I am desperate, I followed the install guide from top to bottom. But no lack. My Canon is dead.

finally I checked [www.linuxprinting.org]("http://www.linuxprinting.org") and there was a solution, 'Do not use Canon' :) so have anybody has idea how ro proceed with Canon or should I go back to shop and change it to e.g. Epson or HP?
Sorry, forget to mention: I use 6.06 Ubuntu ...

---

### Post by Sajmon Phoenix on 2006-08-29
Many thanx for this thread. I searched for this for months. I have Canon LBP 3000 and it works for me.

---

### Post by PPisHere on 2006-08-31
Hi,

Miracle happens - my LBP2900 woke up, I have no idea why.
Now it seems to work :)

---

### Post by crgutierrez on 2007-04-14
> **krokodil said:**
> I have completed the translation, it can be found here:

[https://wiki.ubuntu.com/Canon_LBP_2900_HowTo](https://wiki.ubuntu.com/Canon_LBP_2900_HowTo)

IT WORKS!!!! but very slow and using 100% of the CPU. any idea how to fix that?:D

---

### Post by crgutierrez on 2007-04-14
> **Sajmon Phoenix said:**
> Many thanx for this thread. I searched for this for months. I have Canon LBP 3000 and it works for me.

For me too, but very slow and using 100% of CPU. Any idea how to fix that?

---

### Post by hook69 on 2007-05-21
Thank you very much also from my side!

Installation Instruction works also with LBP-1120!

:popcorn:

---

### Post by silvanus2005 on 2007-08-15
I`m new to Ubuntu, and I have a big problem - can`t make work my printer. I have a Canon LBP 3000 printer, and I tried everything I found on this forum. I also have installed some Linux drivers I found on Canon Australia site, but my printer still doesn`t work at all. Can someone give an idea what to do? I forgot to mention that I`m using the last version of UBUNTU - Feisty Fawn.

---

### Post by Dyliak on 2007-09-01
Thank you very much

I've a LBP 2900 and couldn't understand why was dead after installing drivers! Now works perfectly, thank you again ;)

---

### Post by neozoid on 2007-10-03
thanks all for helping me out

---

### Post by break1979 on 2007-10-10
Thank you for the HOW-TO, it works perfectly! (LBP-2900)

Although here I had to instruct lpadmin to the .ppd file with the full path:

instead of:

```
$ sudo /usr/sbin/lpadmin -p LBP2900 -P CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
```

I used the full path:
```

$ sudo /usr/sbin/lpadmin -p LBP2900 -P /usr/share/cups/model/CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
```


Cheers,

OIli

---

### Post by itsmine on 2007-10-12
Thanks for the instruction, this helps me in solve the problem in Ubuntu 6.06/6.10/7.04, however, it does not work in Ubuntu 7.10 beta/RC, can anyone solve this? Thanks a lot!

P.S.: The error message reported by gnome-cups-manager is "Printing: No %%BoundingBox: comment in header!". or "Ready: /usr/lib/cups/backend/ccp failed"

---

### Post by silvanus2005 on 2007-10-13
I tried again the instructions I found at this addres
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900?highlight=%28CategoryHardware%29](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900?highlight=%28CategoryHardware%29) and my printer LBP 3000  it`s working just fine. 
I installed the drivers i found at the following addres:
[http://alpha03.c-wss.com/inc/ApplServlet?SV=WWUCA900](http://alpha03.c-wss.com/inc/ApplServlet?SV=WWUCA900) and followed the instructios above. I had to mention that I had to switch back to Ubuntu 6.06 in order to install those drivers, I couldn`t install them on Ubuntu 7.04.

---

### Post by mpec82 on 2007-10-19
> **krokodil said:**
> I have completed the translation, it can be found here:

[https://wiki.ubuntu.com/Canon_LBP_2900_HowTo](https://wiki.ubuntu.com/Canon_LBP_2900_HowTo)


Works also with gutsy gibbon?

---

### Post by kolesarm on 2007-10-20
Not for me, anyway... ;(

---

### Post by mpec82 on 2007-10-21
:( Big problem then

---

### Post by Broucek77 on 2007-10-21
i have LBP 2900. In Ubuntu 6.10 a 7.04 it worked good, i installed it by this guide [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900).

 After upgrade from 6.10 to 7.04 it stopped to work, but i reproducet all steps from guide and it worked good.

 After upgrade to Gutsy it stopped work again. [tt]ccpdadmin[/tt] and  [tt]captstatusui -P LBP2900[/tt] shows, that it is ready to print but in fact it don't print...

 Have anybody LBP 2900 working under Ubuntu 7.10?

---

### Post by o_s on 2007-10-22
Canon lbp 1210 not working under Gutsy eather :(

---

### Post by d023961 on 2007-10-22
Hi everybody, 

I faced the same problem after upgrading to Ubuntu 7.10 last weekend. 
Everything went fine except for printing. When I looked into 
/var/log/messages I found strange messages 
like:

audit(1193079100.220:16):  type=1503 operation="inode_permission" requested_mask="w" denied_mask="w" name="/var/ccpd/fifo0" pid=21795 profile="/usr/sbin/cupsd"

I found out that these are caused by ApplicationArmor, a new security tool to grant or deny accees privileges based on program name instead of user name only. 

The profile for CUPSD  is stored in /etc/apparmor.d/usr.sbin.cupsd.

It may work with standard printers directly connected to USB, but the Canon CAPT printing tool requires CUPS to print to a FIFO (
named pipe) from which CAPT then reads and prints to USB. 

I added the following lines (marked with ###insert):

 /var/run/avahi-daemon/socket rw,
  /var/run/cups/ rw,
  /var/run/cups/** rw,
  /var/spool/cups/ rw,
  /var/spool/cups/** rw,
  # needed for Canon CAPT driver ###insert
  /var/ccpd/** rw,                         ###insert

  # third-party printer drivers; no known structure here
  /opt/** rix,


Afterwards do a sudo /etc/init.d/apparmor restart

This solved the problem :)

Best regards,
Andreas

---

### Post by Broucek77 on 2007-10-22
> **d023961 said:**
> Hi everybody, 
This solved the problem :)


 Solved for me too.Thanx a lot!  :lolflag:

---

### Post by Amerikosi-mudaki on 2007-10-23
This method does not work.
I put the net Ubuntu 7.10.
Made as described here https: / / help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900
Then made sudo gedit / etc / apparmor.d / usr.sbin.cupsd
There, I added four lines
> # needed for Canon CAPT driver # # # insert
/ var / ccpd / ** rw, insert # # #

# third printer drivers; no known structure here
/ opt / ** rix,
A click "SAVE"

sudo then wrote / etc / init.d / restart apparmor
but I shall be issued
> ~ $ sudo / etc / init.d / restart apparmor
Reloading AppArmor profiles Skipping profile / etc / apparmor.d / ~ usr.sbin.cupsd
: Warning.

I tried to overload computer.
What should I do???

[COLOR="Silver"]&#1056;&#1086;&#1089;&#1089;&#1080;&#1103;&#1085;&#1077;, &#1087;&#1088;&#1077;&#1074;&#1077;&#1076;![/COLOR]

---

### Post by stavrax on 2007-10-23
i edited the /etc/apparmor.d/usr.sbin.cupsd.
and after i do :sudo /etc/init.d/apparmor restart
i get the message:

Reloading AppArmor profiles  Skipping profile /etc/apparmor.d/usr.sbin.cupsd~: Warning.
:confused:

any ideas?

---

### Post by stavrax on 2007-10-23
Forgot to mention that when i stop the apparmor:

[INDENT]sudo /etc/init.d/apparmor stop
[/INDENT]

The printer is alive 
:)

---

### Post by d023961 on 2007-10-23
Hello, 

make sure you edit the file "usr.sbin.cupsd" and don't create any backup files like "usr.sbin.cupsd~" in directory /etc/apparmor.d/ 
Apparmor will simply execute all profiles found ion this directory and with a backup file you create duplicates. 
Delete the backed up original file if necessary

Regards,
Andreas

---

### Post by sylpub on 2007-10-24
**Does it work when you proceeded with a new installation **and not an upgrade ?
I've done all the steps, I had the same problem with the warning, I deleted the backup files ~ usr.sbin.cupsd...but the printer always  refuses to work.

I notice that :
- there is a dependance problem with the libgtk and the libglib ;for example, if I type the test 
```
captstausui -P LBP2900
```
I obtain 
```
error while loading shared librairies : libgtk-1.2.so.0 : cannot open shared object file : No such file or directory
```
- the ccpd file did not exist, I had to create it too

All others tests work but not the printer. The job remains in queue.

any idea ?

---

### Post by stavrax on 2007-10-28
i had a new installation of ubuntu 7.1 and i had the same problem with libgtk
so i did install the library:
 sudo apt-get install libgtk1.2
(and captstatusui worked just fine.)

---

### Post by Dod_basim on 2007-11-15
can't make it work on 7.10 - 64bit.
i followed the thread and all the "howto"s.
the new 'Document print status' app gives me "Printer 'LBP2900':'cups-missing-filter'."

help please

---

### Post by khanh_coltech on 2008-03-05
```
captstatusui -P LBP1120
```
It show:
> captstatusui Socket Error
Help me.

---

### Post by RussianMan on 2008-03-30
All greetings! 
I have printer Canon 2900 adjusted on [this](http://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900) How-To.
It ceases to work after an output from hiberante.
I am am helped by a command: sudo/etc/init.d/ccpd restart
How to make that it it was carried out automatically after hiberante a computer?

At me Ubuntu 7.10 At a Russian-speaking forum to me anything could not advise. 
And I badly write in English :-(

---

### Post by RussianMan on 2008-03-30
All greetings! 
I have printer Canon 2900 adjusted on [this](http://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900) How-To.
It ceases to work after an output from hiberante.
I am am helped by a command: sudo/etc/init.d/ccpd restart
How to make that it it was carried out automatically after hiberante a computer?

At me Ubuntu 7.10 At a Russian-speaking forum to me anything could not advise. 
And I badly write in English :-(

---

### Post by takjiro on 2008-04-05
Hello, I'm also having problem wihth printing with LBP2900.

Everything is done according to "How-to"
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

But in the last step when I give Code:

captstatusui -P LBP2900

It show:

captstatusui Socket Error

Does anybody know how to fix it?

PC detecdt Canon LBP2900,
But when print, job remain and print never start.

Does someone have idea?

---

### Post by RussianMan on 2008-04-05
Exiting a problem - [http://ubuntuforums.org/showthread.php?p=4617431#post4617431](http://ubuntuforums.org/showthread.php?p=4617431#post4617431)

---

### Post by takjiro on 2008-04-05
Hi, 

I tried your method with input 
command : sudo /etc/init.d/ccpd restart

and now,
command : captstatusui -P LBP2900
have a right response.
With message "ready to print"

Printing proceeded successfully!

Thanks a lot!!

---

### Post by Aoshi99 on 2008-07-10
Hi,

I'm new to both Linux and Ubuntu, and I'm have massive problems setting up my Canon printer. I fear that I have entered some wrong commands since I get various error messages while following your installation guide. I'm really on the edge. My only hope is that they include support for this printer with the next Ubuntu release. But how possible might that be? What shall I do? Keep trying? Or shall I simply wait for the next update?

---

### Post by Frazzle2 on 2008-07-15
I am just trying Ubuntu using the CD and haven't installed it yet.  I am also trying to test print from an LBP2900 and none of the steps from help.ubuntu.com are working: does this mean I would need to actually install Ubuntu to do all that?

---

### Post by Frazzle2 on 2008-07-15
I've even managed to unpack the Debian files sucessfully as the .rpm wouldn't be read by Ubuntu.  Then, when I maange to install what looks like the correct driver for it and try and print a test page, nothing happens as apparently it can't connect to the printer even if it's plugged into the USB and switched on.

---

