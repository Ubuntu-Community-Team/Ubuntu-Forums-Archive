---
title: "Printing to a WinXP machine."
date: 2004-11-04
forum: Hardware &amp; Laptops
---

### Post by -synapse- on 2004-11-04
Right, I have 4 PC's on my home network, 2 are linux and 2 are WinXP.
I want to print to the shared printer connected to the WinXp machine, when I add a printer from the Computer -> System Config menu then sure it prints but is SLOW!
I need it to print at roughly the same speed as if I was printing from a fellow M$ pc.

pwease help me

synapse

---

### Post by mercurus on 2004-11-04
[QUOTE=-synapse-]Right, I have 4 PC's on my home network, 2 are linux and 2 are WinXP.
I want to print to the shared printer connected to the WinXp machine, when I add a printer from the Computer -> System Config menu then sure it prints but is SLOW!
I need it to print at roughly the same speed as if I was printing from a fellow M$ pc.

pwease help me

synapse[/QUOTE]
 I'm not completely sure of my ground here, but from my experience (in reverse: Windows client printing to a Debian server) I think Samba may well have such high overheads as to make snappy printing difficult for all but the fastest of hardware.

I doubt it is completely Ubuntu specific ... there may well be options you can tune in your samba configuration file (smb.conf) to speed up performance. I've not really dealt with a Samba 3.0 installation, so I'd recommend the Samba website and extensive documentation: [http://www.samba.org](http://www.samba.org) ...

My only other suggestion would be to try and swap things around, so the windows machine is a client to the Linux server. How plausible that is, depends on the printer manufacturer and their willingness to produce Linux drivers and support. If that's the road you choose to take, check the printer database at [http://www.linuxprinting.org](http://www.linuxprinting.org) and [http://www.cups.org](http://www.cups.org) .

Cheers
mercurus

---

### Post by -synapse- on 2004-11-04
No, the problem can't be in the samba cfg because it is on a Windows PC. Printing from Windows onto this printer is easy.

cheers 
synapse

---

### Post by -synapse- on 2004-11-04
bump

---

### Post by Magneto on 2004-11-04
for the windows pc attached to the printer

go to start menu---control panel ---add/remove programs - add/remove windows components  under  Other Network File and Print Services  select  Print Services for Unix

that will add a tcpip print service on your windows box

go into the gnome printer config app and add a ipp printer point it to

[http://192.168.5.27/printers/yourprintersname/.printer](http://192.168.5.27/printers/yourprintersname/.printer)

swap your windows pc's ip address and the localname of your printer on that windows pc

this works with cups in general regardless of using gnome printer config app or kde or whatever

---

### Post by -synapse- on 2004-11-05
[QUOTE=Magneto]for the windows pc attached to the printer

go to start menu---control panel ---add/remove programs - add/remove windows components  under  Other Network File and Print Services  select  Print Services for Unix

that will add a tcpip print service on your windows box

go into the gnome printer config app and add a ipp printer point it to

[http://192.168.5.27/printers/yourprintersname/.printer](http://192.168.5.27/printers/yourprintersname/.printer)

swap your windows pc's ip address and the localname of your printer on that windows pc

this works with cups in general regardless of using gnome printer config app or kde or whatever[/QUOTE]
 Right, sorted it now, I just installed the gimp-print driver and now it prints at full speed.

---

### Post by NeoChaosX on 2005-01-23
Bump to say I'm having the same problem synapse was having. However, I tried Magneto's adivce and made an IPP printer, but it doesn't print, even though I have the Print Service for Unix installed on the Windows box. Anyone know of anything else to try?

---

### Post by Geoffers on 2005-01-29
I'm having the same problem too. I have one printer attached to a print server and another attached to my XP box. I ca't print to either!

I have installed Print Services for Unix too, and tried everything that Magneto said.

HEEEELLLLLLPPPPPPPPP!!

---

### Post by DonL on 2005-01-30
I finally got the Ubuntu test page to print to a Canon attached to an XP machine.
But I can't print from any of my applications, like Firefox or OpenOffice.
I get so frustrated with it, I end up leaving it alone for a few weeks between tries.

---

### Post by wernst on 2005-02-21
I got Ubuntu to print on my WIndows XP Printers via the LAN, finally. There are instructions to be found, sort of, at:

[http://www.ubuntulinux.org/wiki/SettingUpSamba](http://www.ubuntulinux.org/wiki/SettingUpSamba)

at the bottom of the page.

I did everything it told me to do, but I did a few things different.

1. I set up a new, password-less user on my XP Machine called "print." I don't like enabling the guest account on Windows machines.

2. steps 6 - 8 call for using the Web GUI for adding a printer, but I used the Gnome printer manager. Set the user to "print" or whatever you want to use here, and leave the password blank.

And bingo, it works.

-Warr

---

### Post by Geoffers on 2005-02-22
Thanks wernst, I'll give that a try.

---

### Post by wernst on 2005-03-17
Well, I've found out one more thing:

You MAY need to manually enter the password for the printer user (on the XP machine) in /etc/cups/printers.conf.

The syntax is:

smb://username:password@computername/printername

if there's no password, then it looks like:

smb://username:@computername/printername

AND you need to restart cupsd for these changes to take effect.

-Warr

---

### Post by woland on 2005-03-19
Following this topic...
I'll soon have 2 computers, one with Ubuntu and other with WinXP. My printer is Canon i550. Canon does not distribute linux drivers for this printer. 
What is the best option, on which mashine I sould install the printer, and to which to share?

---

### Post by buzz75 on 2005-03-21
Another way to set up a printer is to set up your Windows Network first.  Give all your computers (or at least the one you want to print from) a static IP address (i.e., 192.168.0.8) then enable print sharing on your Windows machine.  Next, setup you Ubuntu box with a static IP (Have your router assign it for you).  On Ubuntu, go to Computer > System Configuration > Printing > New Printer > Network Printer > Windows Printer.  Enter the host name, printer name (you can get this information by printing a Test Page from your Windows Machine).  You also need to enter the user name (on you Windows Machine) and the password.  I like what Warr did so I took his suggestion and added “print” as a user on Windows and made it a password free account.  So the user's name was “print” and I left the password blank.  I have a Epson Stylus CX3200 connect to my Windows machine so I chose the Stylus Color drivers (no updates) and it worked great.  

Buzz75  8-[

---

