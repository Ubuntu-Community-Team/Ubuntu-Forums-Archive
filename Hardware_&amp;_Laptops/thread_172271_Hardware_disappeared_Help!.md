---
title: "Hardware disappeared? Help!"
date: 2006-05-08
forum: Hardware &amp; Laptops
---

### Post by yakkob on 2006-05-08
Last night I had my wireless network card working, it was up, it was in Devicemanager and it was present when I typed ndiswrapper -l

This morning I woke up and it was gone!
I even restarted several times last night and it still worked.

Does hardware often disapear in ubuntu or am I the only one?
It is a d-link dwl-g510 with  Marvell W8300 chipset. (rev. a)

Let me know what you need from me so I can get this working.
Thank you.

---

### Post by Rondom on 2006-05-21
Try a ```
sudo modprobe ndiswrapper
``` :-)
Or put ndiswrapper into /etc/modules.

---

### Post by yakkob on 2006-05-21
Hey,
Actually my problem was that the card disappeared from all hardware lists on my computer all together.  It wasn't in device manager and lspci wouldn't show anything either.

So i installed dapper drake and it's there now but ndiswrapper just doesn't seem to work in dapper at all...  i get some fault error and my box locks right up...

Hopefully when dapper comes out it will be working right???

---

### Post by Rondom on 2006-05-21
Does the device work under any other OS as for example Windows?

---

### Post by yakkob on 2006-05-22
Yes it was pulled from a windows machine. It was working fine.
It is showing up in the hardware profiles just fine right now.

It's the ndiswrapper, module that I am having trouble with now. It seems to be a popular problem with dapper drake at this point right now.

I am assuming that it was a hardware conflict in breezy badger that did the disappearing act on me.

I am thinking that I may swap my windows xp onto my desktop and my ubuntu onto my desktop as I only have one license for windows xp...  Then I could more easily run wireless without a router...  This has all been quite a headache for me.  I am just waiting now...

---

