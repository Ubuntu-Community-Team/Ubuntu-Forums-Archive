---
title: "new graphics card Ubuntu screen looks scrambled"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by camaroman1981 on 2009-08-16
Hello all, I upgraded my E machine 3052 with a Agp graphics card. Windows Vista detected it fine But after I installed Ubuntu on my slave drive, when Ubuntu boots up the screen looks scrambled like its not properly detecting the Graphics card. The only thing that looks normal is the mouse on the screen .
 Any help would be great.

---

### Post by oldos2er on 2009-08-16
What make/model card is it?

---

### Post by camaroman1981 on 2009-08-16
> **oldos2er said:**
> What make/model card is it?
 
[ATI Radeon 9600XT AGP 8x 128MB VGA DVI and S Video port]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=110416893860&ssPageName=STRK:MEWNX:IT")
 
I actually was able to finally get distro 8.04 to work. But , when I didt the distro
upgrade all i get is a scrambled screen. You can see the mouse and thats it.

---

### Post by oldos2er on 2009-08-16
> **camaroman1981 said:**
> [ATI Radeon 9600XT AGP 8x 128MB VGA DVI and S Video port]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=110416893860&ssPageName=STRK:MEWNX:IT")
 
I actually was able to finally get distro 8.04 to work. But , when I didt the distro
upgrade all i get is a scrambled screen. You can see the mouse and thats it.

 Unless I'm mistaken (hopefully someone else can verify), ATI no longer supports your card under Linux.

---

### Post by Mark Phelps on 2009-08-17
> **camaroman1981 said:**
> [ATI Radeon 9600XT AGP 8x 128MB VGA DVI and S Video port]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=110416893860&ssPageName=STRK:MEWNX:IT")
 
I actually was able to finally get distro 8.04 to work. But , when I didt the distro
upgrade all i get is a scrambled screen. You can see the mouse and thats it.

If you had restricted drivers installed for ATI, those are no longer supported in 9.04.  You would have to remove them and replace them with the open source drivers.

---

