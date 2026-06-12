---
title: "EW-7711UTn how can I get 802.11n connection?"
date: 2011-01-31
forum: Hardware
---

### Post by magowiz82 on 2011-01-31
Hi,
I'm trying to have a full working 802.11n wireless network (mine router and mine NIC supports it) but using the rt2870sta module provided by kernel 2.6.35-25-generic #44 I can get only a 802.11g connection (54Mb/s), I tried also compiling drivers given by ralink corp but:
- an old one : 2009_1110_RT3070_Linux_STA_v2.1.2.0 doesn't compile
- a recent one : 2011_0107_RT3070_RT3370_Linux_STA_v2.5.0.1_DPO compiles and I can insert the module but the system become instable and I cannot connect to my router.

What can I do?

---

### Post by magowiz82 on 2011-02-01
Searching on web I found that rt2870 driver provided by kernel only supports 802.11b/g connections, so I tried again with latest driver from ralinktech : 
this time I also replaced rt2870.bin firmware with the one provided by ralinktech and it worked.

---

### Post by porker on 2011-04-12
> **magowiz82 said:**
> Searching on web I found that rt2870 driver provided by kernel only supports 802.11b/g connections, so I tried again with latest driver from ralinktech : 
this time I also replaced rt2870.bin firmware with the one provided by ralinktech and it worked.

Can you tell me exactly which driver you downloaded?  I'm currently struggling to get this thing to work at all!!  

Also did you just download them make & make install?

P

---

### Post by magowiz82 on 2011-04-12
> **porker said:**
> Can you tell me exactly which driver you downloaded?  I'm currently struggling to get this thing to work at all!!  

Also did you just download them make & make install?

P
You can find driver here :
[http://www.ralinktech.com/product.php?s=33](http://www.ralinktech.com/product.php?s=33)
the right driver is rt3070

make and make install do the trick but you must first modify some files, instruction on how to modify them can be found in README or INSTALL file inside the archive.

---

### Post by EarthMind on 2011-04-12
Just to let you know: I never manage to get this adapter working properly under linux, I switched to another adapter after a lot of searching and experimenting. And for some reason Windows 7 broke it...

---

