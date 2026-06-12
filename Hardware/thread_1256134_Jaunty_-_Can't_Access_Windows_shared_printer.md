---
title: "Jaunty - Can't Access Windows shared printer"
date: 2009-09-02
forum: Hardware
---

### Post by rick71 on 2009-09-02
I have a W2003 domain with one Jaunty box. My Jaunty box has not been joined to the domain. I have an HP9650 connected to an XP box. The XP box is a member of the domain. My username and password on the Jaunty box is the same as my username and password on the domain.

I can verify the shared printer through Printing. When I try to print a test page I get the following error:

Idle - Tree connect failed (NT_STATUS_ACCESS_DENIED).

When I was using 8.04 I was able to print to to the shared printer.

Does anyone know how I can get this working again?

---

### Post by rick71 on 2009-09-03
I have done an install of 8.10. I still can't print to the printer shared from the Windows XP box.

---

### Post by tacantara on 2009-09-03
I'm not much of a network guy, but have you looked at the settings in Samba to see if anything changed (if you're using Samba)?  I hope to be setting up a wi-fi network within the next few months (2 windows machines and my Ubuntu machine), so I'm trying to find out all about what can go wrong.

---

### Post by rick71 on 2009-09-03
I have the same error messages from fresh installs of both 9.04 and 8.10.

---

### Post by rick71 on 2009-09-06
Bump

---

### Post by dave.johnston on 2011-05-05
Ubuntu 10.04 LTS

Network printing to a windows shared HP LaserJet was working for me but then stopped.  It either stopped due to a software upgrade or when my windows domain password changed.

Either way, I got it working again by doing the following:

**1) sudo vim /etc/samba/smb.conf**

search for 'workgroup' and set the value to be whatever your workgroup/windows domain is.

**2) sudo vim /etc/cups/printers.conf**

search for DeviceURI 
Update the string to contain your domain, username and password e.g.

DeviceURI smb://MYDOMAIN\MyUsername:MyPassword@printerhost/printername

**3) sudo service cups restart**

**4) Print a test page**

---

