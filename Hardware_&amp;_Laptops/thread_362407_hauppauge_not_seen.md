---
title: "hauppauge not seen"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by mrreality13 on 2007-02-15
Hi All,
I want to use mythtv or something close
I am using 6.10 edgy. in a 
amd x2 4200//biostarT- force  6100 (939)//Nvidia 7600gs pci-e(256 megs)//2 gigs ram// 300 gig hd//and a 
Haupauge win-tv  pvr 150 that i got from my friends hp      :popcorn: 

Heres the issue no matter what ive tried  edgy wont "see" the tv card(it shows in bios) any ideas beyond a hammer??

thanx in advance!!

---

### Post by superm1 on 2007-02-15
It isn't seen as in, not on the PCI bus?  If this is the case, you've got hardware problems. 

If you are meaning its not recognized, as in not usable:
Install the driver per this guide: [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

---

### Post by kdub432 on 2007-02-15
type in 'lspci' and see what that says.... you might also want to look at the contents of 'dmesg' for anything having to do with the chip...

---

