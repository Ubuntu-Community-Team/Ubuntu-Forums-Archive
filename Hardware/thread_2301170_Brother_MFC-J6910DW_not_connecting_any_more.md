---
title: "Brother MFC-J6910DW not connecting any more"
date: 2015-10-31
forum: Hardware
---

### Post by Askel on 2015-10-31
Hi

I installed Ubuntu a couple of weeks ago after having used Windows for about 1 year or 2. I tried to install my printer with the driver install tool (witch is new from last time I used Ubuntu) First it worked without any issues. But now something has happened and it won't connect any more. I don't know what I have been doing wrong, and I honestly don't know where to begin. I've reinstalled the printer, but with no luck. It still won't work. Last time I had issues with the firewall. But I opened the necessary ports. And even when I turn of the firewall it still won't connect.

---

### Post by Bucky Ball on 2015-10-31
Using which driver install tool? The one [here]("http://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=mfcj6910dw_all&os=128")? Do you have the machine plugged in via USB or ethernet cable when installing?

---

### Post by Askel on 2015-10-31
Yes that's the one. I thought I put the link in the post but I see that I forgot that. I didn't have the usb-cable connected during the installation. I use wifi to connect to the printer.

---

### Post by Bucky Ball on 2015-10-31
Try deleting all installed printers if you have added any and they are showing in Printers, connect with USB, set everything up (including IP address), and adding printer that way, with it connected, then try it out in the wild world and see if there is a difference.

If you have been connecting wirelessly with it, have you pressed the phyiscal button on the front of the printer and checked the IP and config to make sure that is ok? On mine I press it three times and five, for full print out of config and for summary, can remember which goes with which. ;)

Have you set a static IP on the printer?

---

### Post by Askel on 2015-10-31
Yes, the printer has been set to static IP. I don't know witch button you refer to, but there is a screen on the printer where I checked the IP-adress under Menu/Network/WLAN/TCP/IP. I'll see if I can find the usb-cable, reinstall the printer and then post the results :-)

---

### Post by Askel on 2015-10-31
I've installed it again with USB connected and it works without issues. But I don't know how to set it to wireless again. Also, with the webinterface at [http://localhost:631/printers/MFCJ6910DW](http://localhost:631/printers/MFCJ6910DW) it needs a password to do any changes. What user and password should it be here? I havn't typed any user or password for CUPS. I've tried my username and password and username "root" and my password but it doesn't work.
I also installed it the easy way with "add printers" where drivers for the printer existed. It works fine with USB connected.

---

### Post by Askel on 2015-10-31
I got it to work now. The Device-URI was set to lpd://192.168.010.126/binary_p1. I removed the 0 in 010 and now it worked. I guess that the problem originated from me starting to use UFW after the first printerinstallation, without opening the right ports. When the printer stopped working I didn't know why and reinstalled it and used the above IP. After opening the ports it still wouldn't work because I didn't remove the 0. As said, it's been a while since I used Ubuntu so I'm still a bit rusty :-) Thanks for the help though.

---

### Post by Bucky Ball on 2015-10-31
Great news! Please see the first link in my signature to help others. Good luck and welcome back. :)

---

