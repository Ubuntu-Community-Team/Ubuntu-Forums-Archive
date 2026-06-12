---
title: "[SOLVED] find a printer with an IP address"
date: 2008-07-14
forum: General Help
---

### Post by PGScooter on 2008-07-14
Hi, I am using xubuntu on a laptop and I want to print to a printer which I can easily print to using my windows desktop which is connected to a LAN network. Can I do so wirelessly from xubuntu? I printed out a test page from windows so I have the IP address of the printer.

Is there a utility to help me do this?

Thanks.

---

### Post by cmnorton on 2008-07-14
I'm not sure why wireless has anything to do with this. 

My preference is to add my user to the lpadmin group, and then use [http://localhost:631](http://localhost:631). I've never used Xubuntu's CUPS interface, but Ubuntu's and Kubuntu's CUPS interfaces are quite good.

The question is whether or not you want to use SAMBA to connect to this Windows printer, or if this is a truely networked printer specifiying a jet-direct connection whose port is by default 9100. You can easily set up a jet direct connection from either the CUPS web or Xubuntu CUPS interface.

If you want to go through SAMBA, and you know the printer is shareable, then use smbclient, and you'll need to play with it. I did not find using it all the obvious or easy. Jet direct might not work, unless this printer is a real, standalone network printer.

---

### Post by PGScooter on 2008-07-15
I'm trying to use smbclient but am quite lost; is it hard to explain what I have to do? How do I access the Xubuntu CUPS interface?

---

### Post by plucky on 2008-07-15
> **PGScooter said:**
> I'm trying to use smbclient but am quite lost; is it hard to explain what I have to do? How do I access the Xubuntu CUPS interface?

From Firefox click on the link in **cmnorton's** post [http://localhost:631/](http://localhost:631/) will open the CUPS interface.Make sure the "Show printers shared by other systems" is ticked.


If you know the IP address,you can substitute the IP address for "localhost" in the Firefox address bar,and it should take you to the printer network interface.

Good Luck

---

### Post by danwood76 on 2008-07-15
THat wont work as it is a windows shared printer right?

You need to add it via samba through the cups web interface.

First select 'Add Printer' and follow the instructions selecting 'Windows Printer via Samba' when prompted.

-- edit --

Forgot to say the the device URI will be:
```

smb://WORKGROUP/COMPUTER-NAME/PRINTER-NAME
```

---

### Post by PGScooter on 2008-07-15
thanks a lot for your help, guys.

I'm not sure why, but I was able to add it without samba.. that is, I just went straight to the device and everything worked out fine. I have to mess with the settings cause it keeps printing out large sheets (even though I have A4) but at least I'm printing now.

thanks! I really like the CUPS interface.. easy to use and powerfull options to set.

---

### Post by cmnorton on 2008-07-15
> **PGScooter said:**
> I'm trying to use smbclient but am quite lost; is it hard to explain what I have to do? How do I access the Xubuntu CUPS interface?

Add yourself to the lpadmin group

You can do this easier through the GUI and add yourself to the lpadmin group. (preferable).

Then plug localhost:631 in the address field of your browser. If you are prompted for a password, then use your username's password, because that is now part of lpadmin.

Edit:
-------------------
If you consider this solved, would you mark the thread solved? tnx cmn

---

### Post by PGScooter on 2008-07-15
Ok, I will check that out. Thanks for the help

---

