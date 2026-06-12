---
title: "trouble installing Brother printer on Ubuntu"
date: 2010-07-18
forum: Hardware
---

### Post by jedson3 on 2010-07-18
I am trying to install the Brother MFC-495CW printer on my computer. I use Ubuntu 10.04. I went to Brother Solutions Center, and did all their “before the installation” changes. Then I downloaded their linux-brprinter-installer. I want the printer to work as a wireless connection. When I went through the installer program I hit Y for network users. Then it gave me this choice: 

0: ipp
1: http
2: socket
3: lpd
4: beh
5: serial:/dev/ttyS0?baud=115200
6: smb
7: scsi
8: parallel:/dev/lp0
9: usb://HP/Deskjet%205700?serial=MY4C71X1ZM049M
10: hp:/usb/Deskjet_5700?serial=MY4C71X1ZM049M
11: hpfax
12: Specify IP address.


I have no idea which I should choose. Any help? I put in ipp (O) just because it was first. It didn't work. If I should specify an IP address, what would I use?

Thanks

---

### Post by IcarusR on 2010-07-18
You should be able to get the printer ip address by logging into your router, which should show you all assigned IP addresses .

Check your router manual or google for how to do this.

---

### Post by jedson3 on 2010-07-18
OK. I have my router IP address, and tried inserting it in various ways using the admin/printer program. Nothing seems to work. I guess I don't know how to do it. There is a place for changing the URI device address, but it is not self-evident which of the options I should use here. 

jedson

---

### Post by AlphaLexman on 2010-07-18
I would try a direct connection to one machine first. wether via usb or lpt1, get that working, drivers, kernel, etc., then move on to wireless. You may have to many irons in the fire at once.

---

### Post by wojox on 2010-07-18
Go to System > Administration > Printing

Delete the printer in there.
Click New and it should search for printers.

Now open the Network Printer and select the Brother MFC-495CW (Brother MFC-495CW)
Let it print a test page.

---

### Post by jedson3 on 2010-07-18
Hi --
I had already tried what Wojax suggested. Don't know why it didn't work. But I went ahead and hooked up a usb cable as AlphaLexman suggested, and it works find connected that way. The printer is very close to the computer, so maybe an extra cable is not a big thing. Think I will leave it at this for now. Thanks very much for the help. Will be back for more help if I can't get the Fax to work. 

jedson

---

