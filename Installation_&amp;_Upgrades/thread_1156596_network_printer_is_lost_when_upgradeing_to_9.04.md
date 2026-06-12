---
title: "network printer is lost when upgradeing to 9.04"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by bswan on 2009-05-11
The help says to check the firewall by going to System/Administration/Firewall but there is no Firewall menu item.
I am trying to connect to a printer on a Windows server 2003 box.

I turned off the firewall on the Windows 2003 server but still no network printer. It was working before the upgrade. Ubuntu can not find the printer. The ping to the server is successful.

Bill

---

### Post by pytheas22 on 2009-05-12
You can install the firewall program by typing:
```

sudo apt-get install firestarter
```

and it should then appear in your menu.  But I doubt that's the problem.

How are you trying to connect to the printer?  Did you go to System>Administration>Printing and configure it?  What is the IP address of the printer and what is the IP of your Ubuntu computer?

Also, which version of Ubuntu did you upgrade from and which are you using now?

---

### Post by bswan on 2009-05-12
I am upgrading from 8.10. I did go to the Administration/Printer to try to reset the connection. 

/WORKGROUP/192.168.1.225/MP600 (SMB)

Ubuntu can't find the network printer. 

Bill

---

### Post by bswan on 2009-05-12
Got it! Thanks for the tip. I remove the /WORKGROUP/SERVERNAME/PRINTERNAME  and replace it with the ip/printerName and it now works.

i.e. /192.168.1.225/MP600

Many thanks!
Bill

---

