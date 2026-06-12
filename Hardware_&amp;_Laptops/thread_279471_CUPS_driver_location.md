---
title: "CUPS driver location"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by Quintin Riis on 2006-10-18
What is the location to put Windows printer drivers under Ubuntu?  

/usr/share/cups/drivers/ does not exist by default it seems.

---

### Post by Quintin Riis on 2006-10-18
/var/lib/samba/printers/

Happiness.

---

### Post by kjpus on 2006-10-18
If you are going to use cupsaddsmb to add cups/samba support, you do have to create /usr/share/cups/drivers yourself. cupsaddsmb will look for the drivers there and copy to /var/lig/samba/printers (if that's what you specifiy in the [print$] section in smb.conf).

> **Quintin Riis said:**
> What is the location to put Windows printer drivers under Ubuntu?  

/usr/share/cups/drivers/ does not exist by default it seems.

---

