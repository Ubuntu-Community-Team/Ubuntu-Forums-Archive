---
title: "Sharing HP Deskjet 5440 using CUPS"
date: 2005-11-19
forum: Hardware &amp; Laptops
---

### Post by audax321 on 2005-11-19
Hello,

I have a print server setup using CUPS that has two printers attached to it:

[INDENT]1. HP Deskjet 960C - driver available by default on Linux and Windows[/INDENT]
[INDENT]2. HP Deskjet 5440 - driver needed to be installed for Windows[/INDENT]

Now, the 960C works perfectly when printing from Linux to Linux and Windows to Linux. The 5440 works fine when printing Linux to Linux, but there is a problem with it printing Windows to Linux. When printing within Windows, I can only print from Adobe Acrobat. If I try to print from MS Word, Firefox, etc. the applications just freeze up and I have to end task them. Is there something I can change to get these applications to print or do they use some weird way to print that Adobe Acrobat doesn't?

Thanks for any help. :)

---

### Post by audax321 on 2005-11-22
Okay, I think I figured something out. If I install the HP5440 under windows and select the HP Deskjet 960c driver instead (which is included by default in Windows), printing works perfectly find from any application. So, basically, the solution is to avoid usign the correct driver for the printer. :)

---

### Post by arphe_el on 2005-11-22
hello! please let me know on how to set-up sharing of printer linux to linux ubuntu ditro on the assumption that:

computer A with ip address 192.168.1.101 (server) 
computer B with ip address 192.168.1.102 (client)

it's been a week that i'm trying to figure it out but still out of fortune. also is there any connection with file sharing as well since i'm also having a difficulty on setting this up as well since i'm new to linux but i find ubuntu much more easier to other distro.

Thank you and GODspeed!

---

### Post by audax321 on 2005-11-23
There really shouldn't be much to setup. Unfortunately I'm out of town so I'm going to try to tell you as much from memory as I can :)

ON THE SERVER:
1.  Install the printer on the server.

2.  Edit the file /etc/cups/cupsd.conf:

[INDENT]sudo cp /etc/cups/cupsd.conf_bak (to make a backup)[/INDENT]
[INDENT]sudo gedit /etc/cups/cupsd.conf (to edit the file)[/INDENT]

[INDENT]Find the section called Network Options and you'll notice that it has "#Port 631", remove the # (this will open port 631 on your computer as a listening port for IPP/CUPS)[/INDENT]
[INDENT]Find the section that looks like this:

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

I'm not sure but either add a line that says "Allow From @LOCAL" or replace the "Allow From 127.0.0.1" line with "Allow From @LOCAL" ... the goal here is to allow local network addresses access to the server.
[/INDENT]

ON THE CLIENT:
1.  Go to 192.168.1.101:631 using a browser.

2.  Click the link that says, "Manage Printers"

3.  You should see the printer you installed listed in there. Right click on its name and copy the link location so you have a URI you can paste.

4.  Go to System > Administration > Printing on the client and double click on "New Printer".

5. In the dialog select "Network Printer" and tell it is a "CUPS Printer (IPP)".

6.  Paste the URI in the URI text box and click Next to select the printer make/model, etc. and finish the wizard.

7.  Test the printer and it should work. If not let me know what happens (errors, etc.) and I'll try to figure out what I forget.

:)

---

### Post by KrIaXPaTaLa on 2006-02-06
I'm having the same g**damn problem. Cant install the printer on XP no mather what :S Even tryed that nice driver swapping trick, but it did me no good. The windows spooling service just hangs there, consuming all the processor for as long as I let it run. Basically, a printer exclusive for linux :P

Even thought this was some kind of problem with the fact I'm trying to access a print server, but I've just read a thread about this nice spanish lady with the same problems, connecting the printer directly to the box (via usb).

Any other "driver trick" anyone remembers, please, shoot.

Regards,

KrIaX, Portugal

EDIT: Turns out, the printer works perfectly connected directly to a xp box. The problem seems to be in the fact that I want it shared through a ubuntu machine. Really upseting :\

EDIT 2: Update on the situation - I've now been able to share my printer through samba. But this is extremly inconvenient. Some apps just don't print, others print somethimes, diferent xp computers (exact same version of xp) have diferent reactions to the printer, and it takes forever to detect the printer. Is there anyone out there that has sucessfully shared this printer through cups with a xp box? Just to know it's possible.

---

### Post by KrIaXPaTaLa on 2006-02-12
After manually cleaning the windows registry (as usual uninstalls dont do their work), managed to add the printer as a HP 690c like our friend here. Followed a mail to HP givin them knowledge about this stupid bug. Probably should have sent one to Microsoft too. 

Regards,

KrIaX, Portugal.

---

