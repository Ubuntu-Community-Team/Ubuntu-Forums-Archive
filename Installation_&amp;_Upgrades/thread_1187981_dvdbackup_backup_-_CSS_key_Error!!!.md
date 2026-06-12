---
title: "dvdbackup backup - CSS key Error!!!"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by MacUsers on 2009-06-15
Hi there,
Can any one help me on this please? dvdbackup is not working; I get this error at the end:
```
libdvdread: Error cracking CSS key for /VIDEO_TS/VIDEO_TS.VOB
``` and I get this for al most all the DVDs. It's the blu-ray combo drive; matshita bd-cmb uj-120. Am I missing anything that I need to install in the first place? 
Thanks in advance for your help. cheers!!!

---

### Post by MacUsers on 2009-06-15
No one ever encountered this before? I don't think I'm the only one seeing this. I really appreciate if any one come forward with some help. Cheers!!!

---

### Post by Sub101 on 2009-06-15
Have you installed:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

and have you used the DVD player before? It could be region coded, or yet to have a region set.

---

### Post by MacUsers on 2009-06-16
Hi Sub101,
Thanks for your reply. Yes, I already have install-css.sh installed. I'm not sure whether it's a region issue or due to "FACT". It can't even play region 2 DVDs (I'm from UK). It can play region 0 DVDs but [co]incidentally none of my region free DVDs are copy protected. 

Do you know how to set/change region in Ubuntu. I don't have any fancy desktop installed (but just blackbox) so it should be using CLI or equivalent. Cheers!!!

---

### Post by Sub101 on 2009-06-16
The tool generally used is 

```
sudo apt-get install regionset
```

However I dont know if its command line or not.

---

### Post by MacUsers on 2009-06-16
> **Sub101 said:**
> sudo apt-get install regionset
Thanks!! Let me give it a try. Another question: how do you check the currently set region? Cheers!!!

---

### Post by Sub101 on 2009-06-16
Regionset should tell you the region of your DVD player as well as setting a new one. 

Be careful though, in general you can only change the region of a DVD player a few times

---

### Post by MacUsers on 2009-06-16
Yeah, I figured that out that regionset does that. you were right, there wasn't any region set on the drive:
```
# regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: NONE
vendor resets available: 4
user controlled changes resets available: 5
drive plays discs from region(s):, mask=0xFF
```After setting 2, it plays UK DVD as normal; I just need to figure out if there is any RPC1 firmware out there for my BD-CMB UJ-120 drive. Normally, Matshita/Panasonic very bad in that. Thanks for your help. Cheers!!!

---

