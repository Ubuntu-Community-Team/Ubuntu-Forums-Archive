---
title: "Using Ubuntu as a NAS ?"
date: 2008-10-01
forum: General Help
---

### Post by jetinder on 2008-10-01
I have an old PC with Ubuntu on it, this connected to the internet via a router, on the same router i have my windows PC connected as well (but i need to find out how to make my Windows PC "see and talk" to my Ubuntu PC on the LAN).

In a nut shell i want to use the hard drives on my Ubuntu PC to backup the hard drives on my windows PC.

Can this be done via Ubuntu ?

Can an old PC be used as NAS ?

---

### Post by y@w on 2008-10-01
You can use Samba to share out directories to your Windows machine, or you can use a separate distro such as [OpenFiler]("http://openfiler.com/") or [FreeNAS]("http://freenas.org/") for a true NAS.

---

### Post by jetinder on 2008-10-01
I've heard Samba runs on most Unix and Unix-like systems, such as Linux, Solaris, AIX and the BSD variants, Samba is standard on nearly all distributions of Linux and is commonly included as a basic system service on other Unix-based operating systems as well.

But How do i use SAMBA ?

---

### Post by gpsmikey on 2008-10-01
Samba allows you to share files/partitions with windoze clients.  Check out these links for lots of good information:
[http://samba.org/samba/docs/](http://samba.org/samba/docs/)
[http://www.samba.org/samba/docs/Samba3-ByExample.pdf](http://www.samba.org/samba/docs/Samba3-ByExample.pdf) 
The "Samba-3 by example" link above is a pdf file of the same book by that title you can get from Amazon etc.  Good book - it gives LOTS of examples of configurations - pick one that looks like what you want to do and modify the config file he lists for your own needs ( the config file is smb.conf ).  Once you have  Samba installed and running, your shares will show up in the windows "my network places" when you look.  You can mount shares in windows just like they were on another windows machine too.

mikey

---

### Post by y@w on 2008-10-01
Yeah, you'd really be better off checking out the documentation listed above and asking direct questions.. Samba can do a lot of things, so answering a question that generic would be impossible without writing a book.

---

