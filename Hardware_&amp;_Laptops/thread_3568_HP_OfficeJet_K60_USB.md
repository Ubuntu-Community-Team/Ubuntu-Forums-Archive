---
title: "HP OfficeJet K60 USB"
date: 2004-11-07
forum: Hardware &amp; Laptops
---

### Post by crazypenguin on 2004-11-07
Ok, the printer shows up in the Device Manager, it shows up as detected in the Printers dialog, and it shows up as attached to USB #1.  But, when i try to print a test page, nothing happens.  Any ideas?


EDIT:
OK, it printed like 5 minutes later.  Anyone know why it's taking so long?

---

### Post by az on 2004-11-07
From:Linuxprinting.org
[http://linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_K60](http://linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_K60)

 For printing via USB you NEED to set up this printer with HPOJ, even if you do not want to scan. Only using the modified USB printer.c kernel module from the HPOJ web site does not work with this model.

Now, this is old information.

My usb printer shows up fine in gnome 2.8 because, (I think) Gnome does the checking.  The whole point of HPOJ is to map a particular HP device so that is always accessible at the same place.  If The printer is usb device number 2 today and tomorrow you have your camera connected while you boot, your printer may end up being device number three and then you cannot print.

Now when I set up Ubuntu, hpoj was not there and I could print fine.  It seems to do the detecting on the fly - Very Nice!  WHen I installed hpoj (from universe) the whole thing was buggered up and I could not print until I removed hpoj.

So there may be your problem.  Gnome detecting your printer before your print.

Maybe I am off base or something..

---

### Post by crazypenguin on 2004-11-07
I installed hpoj via synaptic, but it doesn't work at all.  Won't detect the printer.
I tried using the regular printer port so I could use the suggested driver, but then the printer isn't detected by hpoj or gnome.  But the only thing I can do via usb is print a test page..
poo




EDIT
Note to self: printer likes to turn itself off

---

### Post by az on 2004-11-07
"I tried using the regular printer port so I could use the suggested driver"

What does that have to do with the driver.

What driver does it suggest?

Also, some motherboards are funny with printer ports.  Did you plug it in before you booted?

And was the printer on?

Also also, I mentioned hpoj because of the linuxprinting.org page.  I am quite sure that it does not work.  I would recommend that you remove the packages before trying anything else...

---

### Post by Allen S on 2004-11-07
[QUOTE=crazypenguin]I installed hpoj via synaptic, but it doesn't work at all.  Won't detect the printer.
I tried using the regular printer port so I could use the suggested driver, but then the printer isn't detected by hpoj or gnome.  But the only thing I can do via usb is print a test page..
poo


Not sure about the OJ K60 but I have some problems with my PSC-750. After installing HPOJ if it doesn't run ptal-init setup during the install, try running it from a terminal sudo ptal-init setup. 
You can answer NO on scan parallel ports & Yes for scan USB ports. It should then detect the printer and suggest a name, pick the defaults from here on out. This allowed the scanner to work, but still no printing.

For what ever reason it took a reboot, then I went to Printers and setup the printer, my model was listed. From that point on both the printer and scanner worked. Now my PSC-750 is always plugged into the same USB port. I would think that if you moved it to a different USB port you would have to go through the setup again, not sure.

Allen

---

### Post by crazypenguin on 2004-11-08
It's fixed now.
The scanner doesn't matter, it doesn't work anyway.

---

### Post by az on 2004-11-08
What did you do?

---

### Post by crazypenguin on 2004-11-10
Somewhere along the line, the printer decided to turn itself off, so it wasn't being recognized by the computer.  I hooked it up using the printer port so I wouldn'thave to worry about hpoj and rebooted and it's fine.

---

### Post by stimpyaw on 2007-01-28
> **azz said:**
> From:Linuxprinting.org
[http://linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_K60](http://linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_K60)

 For printing via USB you NEED to set up this printer with HPOJ, even if you do not want to scan. Only using the modified USB printer.c kernel module from the HPOJ web site does not work with this model.

Now, this is old information.

My usb printer shows up fine in gnome 2.8 because, (I think) Gnome does the checking.  The whole point of HPOJ is to map a particular HP device so that is always accessible at the same place.  If The printer is usb device number 2 today and tomorrow you have your camera connected while you boot, your printer may end up being device number three and then you cannot print.

Now when I set up Ubuntu, hpoj was not there and I could print fine.  It seems to do the detecting on the fly - Very Nice!  WHen I installed hpoj (from universe) the whole thing was buggered up and I could not print until I removed hpoj.

So there may be your problem.  Gnome detecting your printer before your print.

Maybe I am off base or something..

I'm having the same problem with my HP OfficeJet K60 printer.  When I 1st installed Ubuntu and sent a printer test page it worked.:)   I then wanted to setup the extra features of the K60 (fax, scan, copy).  I downloaded (hplip-1.6.12.tar.gz) from [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/).  Once I installed that package, the K60 would not print any longer.  The only way the HPLIP interface works is that you have to have the K60 installed.  I did try using the different K60's the New Printer wizard found.  And that did not help either.
I tried your suggestions by uninstalling HPOJ and also HPLIP and K60 still will not print like it did when I 1st installed Ubuntu.:(

Any other suggestions would be great help to this newbee to Ubuntu.](*,)

---

### Post by 11hjpphty76lkjj on 2007-01-29
Do not use HPOJ.  It's old--outdated--and will make hplip not function correctly. 

Remove hpoj, re-install HPLIP and the printer should function.

Also configure the printer using the hp-setup application as this will correctly configure the printer for your system using the hp backend.

---

### Post by stimpyaw on 2007-02-05
I uninstalled HPOJ and HPLIP.  I went to [http://hplip.sf.net/](http://hplip.sf.net/) and dowloaded "hplip-1.7.1.run" and followed the install instructions from [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html) and I got to the screen "Select/Confirm PDD File".  I click on the next button and I get and pop-up window that has a red circle with a white "x" and says 

Device I/O Error
Could not communicate with device. Device may be busy.
Retry  Cancel

I click on the retry button and the same pop-up repears.  As a side note the printer works fine on my Windows XP can.  Is there anything else I could try to get this to work?

Thanks for your help on this issue.

---

### Post by 11hjpphty76lkjj on 2007-02-05
Run:

sudo tail -f /var/log/messages

and then in another terminal:

sudo hp-setup -g 

send the output from both.

A

---

### Post by stimpyaw on 2007-02-06
ok, I ran both command strings and the outcome:

1st attachment is for the command string >sudo tail -f /var/log/messages<.
   ~ I did a ctrl-c after the second command string finished.

2nd attachment is for the command string >sudo hp-setup -g<.
   ~ after this command completed the printer starting to print a test page.  The title of the page is "HP Printer Test Page".  It has a picture on it, two info boxes one called "Imageable Area" and "Printer Information".  At the bottom of the page it says "Printed Using HP Linux Imaging and Printing System" with the HP logo to the lower right.

Does this mean the printer is now setup to work correctly?  Will I be able to Fax, Copy, Scan and Print from within Ubuntu? I check the System > Administration > Printing and I have to printer icons.
               ~ OfficeJet_K60 [COLOR=Navy]Ready
[/COLOR]               ~ OfficeJet_K60_fax [COLOR=Navy]Ready
[/COLOR]               ~ OfficeJet_K60_2 [COLOR=Navy]Ready
[/COLOR]               ~ OfficeJet_K60_fax_2 [COLOR=Navy]Ready[/COLOR]
I removed the icons that had the "_2".  I did a test print from, OfficeJet_K60 and OfficeJet_K60_2, and the printer printed 2 test pages.  Should I have left the 2 extra icons?

I'm going to restart my system and then send a test page to see if it works.

THANK YOU for your help in this matter!!

---

### Post by 11hjpphty76lkjj on 2007-02-06
Yeah you should be all set. :)

A

---

### Post by stimpyaw on 2007-02-07
THANK YOU! For all your help in getting my HP OJ K60 working.

---

### Post by rush242 on 2007-08-08
> **kalosaurusrex said:**
> Run:

sudo tail -f /var/log/messages

and then in another terminal:

sudo hp-setup -g 

send the output from both.

A
OK, so now I get to play this game, D'oh!!

 I've tried CUPS, HPJIS, OpenPrinting and the stuff in this thread. I get nothing. Oh I can add that same K60 as many times as I wish, and none of them will print. I can take them off and replace them in the various ways, and all goes well, they just never print.

I tried:

sudo tail -f /var/log/messages

I got:

Aug 8 10:18:46 rush-desktop -- MARK --
Aug 8 10:38:48 rush-desktop -- MARK --
Aug 8 10:58:50 rush-desktop -- MARK --
Aug 8 11:18:50 rush-desktop -- MARK --
Aug 8 11:38:50 rush-desktop -- MARK --
Aug 8 11:58:50 rush-desktop -- MARK --
Aug 8 12:18:52 rush-desktop -- MARK --
Aug 8 12:38:53 rush-desktop -- MARK --
Aug 8 12:47:49 rush-desktop hp: unable to open /var/run/hpssd.port: No such file or directory: api/hplip_api.c 103
Aug 8 12:47:49 rush-desktop hp: unable to connect hpssd socket 2207: Connection refused: api/hplip_api.c 738

Whereas it stopped and I had to ctrl-c it.

Then, sudo hp-setup -g, And got:

HP Linux Imaging and Printing System (ver. 2.7.7)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 154
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device
Unable to connect to HPLIP I/O (hpssd).
hp-setup[4949]: debug: Exception: 96 (Unable to contact service)
error: Unable to connect to HPLIP I/O. Please (re)start HPLIP and try again.

The printer works fine, it's plugged in, I've tried other USB ports and it works fine on XP PCs. CUPS just adds it again, and none of them will print, even when I provide the "HP-OfficeJet_K60-hpijs.ppd" file. Open Printing and HPJIS works fine too, well, except that it doesn't print.

There is one error I "found," whenever update manager adds an update, it adds the new update fine and then I get this:

Errors were encountered while processing:
hplip
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up hplip (1.7.3-ubuntu1) ...
Creating/updating hplip user account...
* Starting HP Linux Printing and Imaging System
...fail!!
invoke-rc.d: initscript hplip, action "start" failed.
dkpg: error processing hplip (--configure):
subprocess post-installation script returned error exit status 1

Any thoughts anyone? I'm a COMPLETE newb to this Linux stuff, but I'm trying to master the learning curve. This one, however seems to have mastered me. D'oh!!

Thanks for any advice, thoughts or guidance!

Rush

---

### Post by rush242 on 2007-08-08
Here's a thought, could CUPS be conflicting with HPLIP? Is that possible?

I mean should there only be one or the other on the machine, or is CUPS part of Ubuntu and it doesn't matter if HPLIP is installed as well. When I go into Services both Cupssys and HPLIP are running.
 
Thoughts?

---

### Post by 11hjpphty76lkjj on 2007-08-09
Can you run:

cat /etc/hosts

and post the output?

and no CUPS and HPLIP work well together.

A

---

### Post by rush242 on 2007-08-22
Thanks for the help, A.

When I run that command, I end up with:

```
127.0.0.1       localhost
127.0.1.1       rush-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Needless to say, I have no idea there. 8^]

---

### Post by rush242 on 2007-08-24
Anyone have any thoughts regarding the error messages when any updates are installed?

```
Errors were encountered while processing:
hplip
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up hplip (1.7.3-ubuntu1) ...
Creating/updating hplip user account...
* Starting HP Linux Printing and Imaging System
...fail!!
invoke-rc.d: initscript hplip, action "start" failed.
dkpg: error processing hplip (--configure):
subprocess post-installation script returned error exit status 1
```

Something there ain't right...

Thanks in advance.

---

### Post by rush242 on 2007-08-28
Anyone, anyone, Bueller?

Gracias...

---

