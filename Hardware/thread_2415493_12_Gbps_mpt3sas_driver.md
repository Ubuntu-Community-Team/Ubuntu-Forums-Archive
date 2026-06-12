---
title: "12 Gbps mpt3sas driver?"
date: 2019-03-26
forum: Hardware
---

### Post by scjones5 on 2019-03-26
Hello, 

I am trying to connect my 18.04 LTS server to a storage array with SAS cables. I have the 12 Gbps HBA card, but I don't believe Ubuntu has the requisite driver in order for me to see the array. 

Or, at least, I think what I need is an updated mpt3sas driver - it appears that 18.04 has version 17.100.00.00, which is very much out-of-date. 

Does such a driver exist? Can I compile an updated one from scratch? Both the server and the array are Dell products - has anyone ever successfully integrated the two?

Thanks in advance, 

Scott

---

### Post by scjones5 on 2019-03-28
The card in question seems to be a [FONT=Tahoma]LSI Logic / Symbios Logic SAS3008 PCI-Express Fusion-MPT SAS-3[/FONT]

---

### Post by Yellow Pasque on 2019-03-28
Is it possible for you to try an updated kernel on the server? That would be the easiest way to see if a newer version of the mpt3sas module/driver fixes your problem. If you try a 5.0.x kernel, it should have mpt3sas 27.101.00.00

---

### Post by scjones5 on 2019-03-28
Thanks, I may give that a try. However, it looks like mpr might be the driver that supports this card: [http://manpages.ubuntu.com/manpages/bionic/man4/mpr.4freebsd.html#name](http://manpages.ubuntu.com/manpages/bionic/man4/mpr.4freebsd.html#name)

However, I don't know how to install this driver on Ubuntu...

---

### Post by Yellow Pasque on 2019-03-29
You're running a FreeBSD kernel? Sorry, but you lost me...

---

