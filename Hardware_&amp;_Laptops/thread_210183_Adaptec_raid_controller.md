---
title: "Adaptec raid controller"
date: 2006-07-06
forum: Hardware &amp; Laptops
---

### Post by jjx on 2006-07-06
I am trying to install ubuntu 6.06 to a pc having an adaptec raid controller.
Both hard disks are connected directly to the adapter.
The problem is that ubuntu isnt recognizing the hard disks, obvioulsy because is missing the controller drivers. So i cant even install to one hard disk and use software raid later.

**lspci -n** shows:
> 0000:03:04:0 raid bus controller: Adaptec unknow device 043f (rev 08 )


Any idea where to find drivers for adaptec? I cant find something usefull on their site...

Any help will be appreciated

---

