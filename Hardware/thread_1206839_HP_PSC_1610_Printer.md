---
title: "HP PSC 1610 Printer"
date: 2009-07-07
forum: Hardware
---

### Post by tksu22 on 2009-07-07
Hello. I've recently installed the Ubuntu 9.04 Server Edition on an older desktop and for file sharing it runs awesome. I'm using it as a LAMP server and Samba is up and running. 
However, I would also like to make it a print server and I am having a ton of trouble with it. So far I have CUPS running and it can print a test page to the HP PSC 1610 printer connected to it through USB. I can do this from the CUPS interface on my Vista machine with servername:631. But I can't get anything from a Windows computer to print to it. I can see the printer on my Windows machine but then when I open the printer, it says Access Denied, Unable to connect. I've tried a bunch of stuff to no prevail for the last week or so. Any help?

---

### Post by shatterblast on 2009-07-07
In a Microsoft environment, a user needs at least Power User access to print from non-M$ systems.

---

### Post by tksu22 on 2009-07-07
I am an administrator on my Vista machine.

---

### Post by tksu22 on 2009-07-07
Also, a lot of forums require that cupsys be restarted by using:
sudo /etc/init.d/cupsys restart

but I don't have cupsys in my init.d folder. The closest is /etc/init.d/cups
Is this the same thing?

---

### Post by tksu22 on 2009-07-08
Also, I am not very sure about the path that the hp psc printer should go to under SAMBA. Is /var/spool/samba correct? Even if I am using CUPS as well? because I see a folder called /var/spool/cups also.

---

### Post by shatterblast on 2009-07-08
> **tksu22 said:**
> Also, a lot of forums require that cupsys be restarted by using:
sudo /etc/init.d/cupsys restart

but I don't have cupsys in my init.d folder. The closest is /etc/init.d/cups
Is this the same thing?

Yes, I believe it is.  I think the name change is fairly recent.

Also, this may help you:

[https://help.ubuntu.com/community/SettingUpSamba#Sharing%20CUPS%20Printers](https://help.ubuntu.com/community/SettingUpSamba#Sharing%20CUPS%20Printers)

The Power User item works for XP, but I think an extra item exists in Vista that I'm unaware of.

---

### Post by tksu22 on 2009-07-09
Is nobody.nobody now nobody.nogroup? Is that the same thing. Because I saw that I needed to change the permissions of /var/spool/samba to the user nobody.

---

### Post by shatterblast on 2009-07-09
> **tksu22 said:**
> Is nobody.nobody now nobody.nogroup? Is that the same thing. Because I saw that I needed to change the permissions of /var/spool/samba to the user nobody.

No, they are not the same.  Those two are Linux classifications for security permissions.  I suggest updating your software since you're asking that question.

---

