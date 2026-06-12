---
title: "Problem printing to networked printer on ubuntu from winXP"
date: 2005-10-02
forum: Hardware &amp; Laptops
---

### Post by pospeselr on 2005-10-02
I can see my printer (HP Photosmart 7660) from windows, but whenever I try to connect to it I get a dialoge claiming that "The server for the printer does not have the correct printer driver installed".  It then goes to a dialoge with a listing of possible printer drivers to choose from, but mine is not on the  list.  I'm using the hplip driver and my printer workes perfectly from ubuntu.  Here is my smb.conf file:

/////////////////////smb.conf/////////////////////
[global]
workgroup = MENTOK
security = share
printing = cups
printcap name = cups

[printers]
comment = Printer on VULTURO
path = /var/spool/samba
browsable = no
guest ok = yes
writable = no
printable = yes

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

//////////////////////////////////////////////////////

The path for the printer drivers contains two folders, W32X86 and WIN40, both of which are empty.  I left it too that path since that what it seemed to default to when I installed samba.

I'm running off a server installationi with the following packages:
x-window-system-core
kdebase
kdm
samba
kdenetwork-filesharing
hplip
foomatic-db-hpijs
foomatic-bin

Any ideas?

---

