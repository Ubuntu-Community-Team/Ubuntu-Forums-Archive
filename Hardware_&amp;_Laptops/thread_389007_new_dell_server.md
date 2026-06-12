---
title: "new dell server"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by trueegor on 2007-03-20
I am fairly new to Linux.  I have played with Ubuntu (Edgy) on an older machine and am impressed.  

I am going to buy a new file/print server and am thinking Ubuntu.  I am currently looking at a Dell PowerEdge with Core2Duo processor and Raid.  

Probably too general of a question, but is Ubuntu likely to have the drivers for the hardware or would I be better off letting Dell install Red Hat.  

Thanks

---

### Post by apjone on 2007-03-20
Recently we bought a server from dell and no version of ubuntu would install due to not having drivers for the raid card. Please check the card against the list of compatible hardware.

[http://doc.gwos.org/index.php/Dell](http://doc.gwos.org/index.php/Dell)

---

### Post by trueegor on 2007-03-20
Has anyone been successful at getting the SAS 5iR raid controller to work with Ubuntu.  I'm not finding it in the Hardware compatibility list.  

Thanks

---

### Post by huuan on 2007-06-20
I have gentoo installed on a poweredge 840 with sas 5ir and the driver for the sas I used was

**Fusion MPT ScsiHost drivers for SAS**

which works just fine I expect that ubuntu has that driver and that you just didn't know that's what you needed.

Hope that helps.

:popcorn:

---

