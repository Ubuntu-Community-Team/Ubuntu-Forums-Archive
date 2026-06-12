---
title: "Hardy on a USB Key"
date: 2008-09-03
forum: Hardware
---

### Post by wbascus on 2008-09-03
HI guys. 

I wanted to install a development environment on a USB key that I could use while commuting, when I have to use different computers on different days, and don't have access to the internet.  

My boxes include a Thinkpad T60p and Dell Latitude D630 with the standard video card.  I bought a 4GB Sandisk Cruzer, and installed Hardy off of the live CD.  

My problem is that hardy runs very slowly off of the USB key.  If this is normal, I'll accept it;  I just don't have any frame of reference, so I was hoping that people could tell me a) if this is normal and b) why this happens. 

Thanks, 

Bill

---

### Post by mrsteveman1 on 2008-09-03
It is slow if you run it as a full installed system.

If you just copy the files from the ISO to the key (vfat filesystem) and install syslinux, its faster because reads from the key are compressed (you can uncompress faster than you can read from flash).

You can also setup persistence like this so you get the advantages of both the compression and persistent changes.

---

