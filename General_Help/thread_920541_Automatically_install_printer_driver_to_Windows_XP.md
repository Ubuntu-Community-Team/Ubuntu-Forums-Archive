---
title: "Automatically install printer driver to Windows XP"
date: 2008-09-15
forum: General Help
---

### Post by takeikos on 2008-09-15
I'm using network printer through Ubuntu 7.10 server.
Samba and CUPS were already installed and configured.
I can print out from both Ubuntu server and Windows XP.
But I need to install Windows printer dirver manually to Windows XP for the moment. 

When I select network printer in 'Printers and Faxes' 
in control panel -> 'A network printer or...' -> Browse for a
printer',the below warning shows up.
--------------------------------------------------------------
The server for the printer does not have the correct printer
driver installed.If you want to search for the proper driver,
click OK. Otherwise, click Cancel and contact your network
administrator or original equipment manufacturer for the 
correct printer driver.
--------------------------------------------------------------
Then click OK, I can install Windows driver [COLOR="Blue"]manually[/COLOR].

So my ideal is to [COLOR="red"]automatically[/COLOR] install
the network printer driver when selecting network printer.

I put Windows driver in /var/lib/samba/printer, but it still
fails. The below is my smb.conf relating to printer:

```

[global]
   load printers = yes
   printing = cups
   printcap name = cups
&#12288;&#12288;printer admin = @lpadmin
&#12288;disable spoolss = no
&#12288;use client driver = no

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   create mode = 0700
   guest ok = yes

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printer
   browseable = yes
   read only = yes
   guest ok = yes
   write list = root, @ntadmin, @lpadmin


```

I'd greatly appreciated it if you could give me some hints to automatically install windows driver through samba/cups on
Ubuntu 7.10 server. Thank you in advance.

Samba : 3.0.26
CUPS  : 1.3.2
Printer : HP LaserJet P2015n

---

### Post by wolfteeth on 2009-04-22
I am raising the same question and see if anyone who can help? thanks.

---

### Post by frankytea on 2009-09-04
This is exactly my problem too. Folks at work would break if they needed to manually install the drivers.

It should be possible to map the necessary drivers in the path written under printer$ in smb.conf. Afterall, that's what its there for right?

---

