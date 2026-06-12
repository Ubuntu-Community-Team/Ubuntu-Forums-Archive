---
title: "Connect to network printer"
date: 2005-11-22
forum: General Help
---

### Post by immoral giant on 2005-11-22
I have a printer that is shared on my other computer which is running Windows 2000 Professional.  Is there any way for me to be able to print off it through the network.  I can access the shared folders on the 2000 machine, but not the printer.

The printer is a Lexmark X5500.


Thanks

---

### Post by tim15856 on 2005-11-22
Haven't tried it myself, but in printer manager, if Ubuntu comes with the driver, you should be able to 'add printer'. Then select 'smb' for the port. I believe it should then ask for the server, share name, user name, and password to connect.

---

### Post by immoral giant on 2005-11-23
I have got that far, and connected to the computer it is on, but there is no printer in the printer drop down box.  Is this just because there is no linux driver then?

---

### Post by immoral giant on 2005-11-27
Bump, is this just a lack of linux support from lexmark?

---

### Post by artinla on 2006-09-14
You need to enable the "Guest" user on the windows machine, then you need to make sure you have the "Detect LAN printers" enabled under "Global Settings" in the printing control panel of Ubuntu.  Enter the username "Guest" and no PW.

2000 is a pain in the a$$, some printers must be run as LPR's.  That requires installing "Print services for Unix" in 2000.

---

