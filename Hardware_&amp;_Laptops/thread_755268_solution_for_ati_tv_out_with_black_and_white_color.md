---
title: "solution for ati tv out with black and white colors"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by SOME1 on 2008-04-14
hi, 

I have a laptop (ibm t43p) with ati graphic card and svideo output. 
I also have a very old tv, and I try for a long long time to solve a problem - I can not see the computer output on the tv in colors. 
I searched so many forums, look for many threads and tried every thing I noticed, I also changed the cables with new cables... and nothing. the output is still in black and white. 

until now - 

i check the ati help option in the terminal and according to it I found a very simple solution - 

I typed on terminal 

```
sudo sudo aticonfig --tv-standard-type=VIDEO
```

restart the computer.. and I CANT BELIEVE IT.. it worked! 

I am using ati restricted drivers from ati site on ubuntu 7.10. 

this is the section of xorg.conf on my computer now - 
```
Section "Device"
	Identifier  "ATI Technologies Inc M24GL [Mobility FireGL V3200]"
	Driver      "fglrx"
	Option	    "TVFormat" "PAL-B"
	Option	    "TVStandard" "VIDEO"
EndSection
```
I hope it will help someone else too. 
good luck.

---

### Post by Trollslayer on 2008-04-14
Is the TV format correct for your country? There are a lot of variations on PAL, the UK is PAL-I for example. Check on Wikepdia for the correct format.

---

