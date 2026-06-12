---
title: "Sharing printer without internet connection"
date: 2009-12-15
forum: Hardware
---

### Post by Karisma on 2009-12-15
Hi all,
Can i access a printer attached on a remote ubuntu system from another ubuntu pc without using internet connection? The computers were connected by LAN. Any advise will be greatly appreciated:)

---

### Post by IcarusR on 2009-12-15
Depends what you mean by 'remote' If both boxes are networked together on the same site. ie on the same local network (LAN)
Check out this page for instructions.

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

---

### Post by Karisma on 2009-12-16
> **IcarusR said:**
> Depends what you mean by 'remote' If both boxes are networked together on the same site. ie on the same local network (LAN)
Check out this page for instructions.

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

thanks for the reply :)
i had tried it before and it worked using ipp. however, it can't be used without connection to internet. the boxes are networked using LAN cable.

---

### Post by IcarusR on 2009-12-17
Strange because I've just setup a printer that is attached to my LAN server using that very document. Both boxes are running Ubuntu 8.10. I do have Internet access but that is NOT necessary.

The device uri is 
> ipp://192.168.1.65:631/printers/Epson-Stylus-COLOR-600

The printer is also listed on the cups web interface at

[http://127.0.0.1:631]("http://127.0.0.1:631")

I had to set the printer up on the server so it prints from it. Then the printer pops up in the 'Printer Configuration' app as an available printer.

I suggest you have another go.

---

### Post by Karisma on 2009-12-17
> **IcarusR said:**
> Strange because I've just setup a printer that is attached to my LAN server using that very document. Both boxes are running Ubuntu 8.10. I do have Internet access but that is NOT necessary.

The device uri is 


The printer is also listed on the cups web interface at

[http://127.0.0.1:631]("http://127.0.0.1:631")

I had to set the printer up on the server so it prints from it. Then the printer pops up in the 'Printer Configuration' app as an available printer.

I suggest you have another go.

Would you tell me how did you build your LAN and LAN Server?  does it need internet connection to connect one box to another?
I'm not so sure, but i think i'm going to use Samba. but i don't know if it uses internet or not

---

### Post by sgosnell on 2009-12-17
Samba will work, and it doesn't need an internet connection.  The easiest way is to use a printer that has an ethernet interface, and connect it to a router connecting the computers, but you can make it work with a USB printer connected to a computer.  An internet connection is not an essential part of a LAN.

---

### Post by LinuxDeal on 2009-12-17
One thing that [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) doesn't mention is that you need to mark each printer you want to share as shared.

Open the printer configuration system > admin > printing
right click on the printer you want to share
select properties
select policies
check the box "shared"

That should do it.

Enjoy!

EDIT: I just added the additional instruction to the documentation ;]

---

### Post by IcarusR on 2009-12-19
> Would you tell me how did you build your LAN and LAN Server? does it need internet connection to connect one box to another?
I'm not so sure, but i think i'm going to use Samba. but i don't know if it uses internet or not

I have a home server in the cupboard, which it connected to my router (also adsl modem). My laptops connect to router by wifi. 
Internet is not necessary for any of my LAN (local area network) to work, including printing.

The printer has to be setup & working on the box it is connected to in order for it to be visible elsewhere on the network.

Samba is not easy to setup, that's why I don't use it for printer. Cups is easier in my opinion & you get a nice web interface for management.

---

### Post by Karisma on 2009-12-20
> **IcarusR said:**
> I have a home server in the cupboard, which it connected to my router (also adsl modem). My laptops connect to router by wifi. 
Internet is not necessary for any of my LAN (local area network) to work, including printing.

The printer has to be setup & working on the box it is connected to in order for it to be visible elsewhere on the network.

Samba is not easy to setup, that's why I don't use it for printer. Cups is easier in my opinion & you get a nice web interface for management.

how is the printer addressed in the client box? does it use ipp?

---

### Post by Karisma on 2009-12-20
> **LinuxDeal said:**
> One thing that [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) doesn't mention is that you need to mark each printer you want to share as shared.

Open the printer configuration system > admin > printing
right click on the printer you want to share
select properties
select policies
check the box "shared"

That should do it.

Enjoy!

EDIT: I just added the additional instruction to the documentation ;]

i don't know if i have checked it or not. i have not seen the LAN again since around last week (they're not mine). but the client box was enable to access the print server. the problem is, it needed internet connection.

---

### Post by Karisma on 2009-12-20
> **sgosnell said:**
> Samba will work, and it doesn't need an internet connection.  The easiest way is to use a printer that has an ethernet interface, and connect it to a router connecting the computers, but you can make it work with a USB printer connected to a computer.  An internet connection is not an essential part of a LAN.

well, since i'm still new with this, maybe i'd better to cancel using Samba. maybe i need to try something i sure i will be able to understand. i had tried using SSH to alter the internet connection. but when i tried to start it in command line, it asked for password. i didn't know which password did it ask for because it didn't work with the user's password.

---

### Post by IcarusR on 2009-12-20
> how is the printer addressed in the client box? does it use ipp?

Yes it uses ipp

> Device URI: ipp://192.168.1.65:631/printers/Stylus-COLOR-600 

I have set my printer up using the instructions on the page I linked.

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

Once that is done the printer itself does not need to be setup on the client box. It just appears. Then one can manage it from cups web interface.

Can you explain your LAN setup to us please, to clarify things ?
Are all boxes in the same building all connected via ethernet or wireless ?

---

