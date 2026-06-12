---
title: "Enable Read/Write on External NTFS/Fat Filesystem"
date: 2008-04-24
forum: Hardware
---

### Post by angrashak on 2008-04-24
Hi,

I have auto mounted an external USB NTFS hard disk to my Ubuntu desktop. The problem is I cannot write to the hard disk even when using the root account.
I have made the following entry into my fstab but that didn't help

/dev/sdc1       /media/NT2500   auto    rw,users,defaults,umask=000  0      0


any idea on how I can write into the external hard disk ?

Thanks in advance.

---

### Post by the3dman on 2008-12-07
What version of Ubuntu Are you using?

---

### Post by samuraix51 on 2008-12-08
look at ntfs-3g that will allow you to read and write to NTFS partitions, I've used it and haven't had any issues.

---

### Post by phiredesign on 2008-12-08
That worked great, thank you very much. I am however having another problem at the moment. My network is installed (I am using ATT and a 2wire wireless modem), but I still cannot connect. I have pinged the router and it turns out fine, and I think my setting are right, but still no connection.
SSID: 2WIRE927
Mode: Infrastructure
BSSID: blank
MAC Address: blank
Security: WEP 40/128-bit Key
Key: 6767676767 (custom key for testing connection)
WEP Index: 1
Authentication: Shared Key


Should any of this be changed? Thank you for all of the help.

---

### Post by razy60 on 2008-12-08
You need to fill in: MAC address, possibly bssid, and whatever security settings you have set.
 At the moment from your post the router is not seeing your PC.

Raz

---

