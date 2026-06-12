---
title: "Formatting SD Cards"
date: 2008-04-23
forum: Hardware
---

### Post by rbradt on 2008-04-23
I have a mini SD Card, and my laptop reads it just find.  As far as I can tell, I am able to delete files from the card, but I was wondering if there were any actual formatting utilities for Ubuntu???  Any ideas?  

Thanks ahead of time!

---

### Post by Limpan on 2008-04-23
Try Gparted. It's in the repositories.

---

### Post by PmDematagoda on 2008-04-23
Install Gparted using:-
```
sudo apt-get install gparted
```

After installation Gparted can be run from System>Administration>Partition Editor and you can format the SD card from that.

---

### Post by rbradt on 2008-04-23
Thanks a lot to the both of you!!  Gparted was exactly what I was looking for!

---

### Post by wellybelly on 2009-09-22
Hi,

I had some trouble with gparted mounting and unmounting the SD card, but this forum post:
[http://groups.google.com/group/beagleboard/browse_thread/thread/2e054693dca41e38](http://groups.google.com/group/beagleboard/browse_thread/thread/2e054693dca41e38)

explains another way to do it, using mkfs.

---

