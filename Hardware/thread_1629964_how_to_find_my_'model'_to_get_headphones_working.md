---
title: "how to find my 'model' to get headphones working?"
date: 2010-11-24
forum: Hardware
---

### Post by Scooter_X on 2010-11-24
I have read a lot on how to get my headphones going when I plug them in, but the only thing is that I don't know how to find my 'model' to put at the end of the "/etc/modprobe.d/alsa-base.conf" where it says "options snd-hda-intel model=   "

I remember having read about how to find that somewhere on the internet, but haven't been able to find it again. :oops:

Can someone please tell me how to make terminal tell me what model I need to put there?

---

### Post by dsd_inc123 on 2010-11-24
:)

nooo idea :( sorry pal :(

-------------------------------------

[accpac](http://www.dsdinc.com/products/sage-abra/index.html),[mas500](http://www.dsdinc.com/products/sage-payment-solutions/index.html),[fas software](http://www.dsdinc.com/products/sage-fas-fixed-asset-mgmt/index.html),[mas 500](http://www.dsdinc.com/products/sage-mas-500-erp/index.html),[saleslogix](http://www.dsdinc.com/mas200/index.html?category_one=products&amp;category_two=mas200&amp;page=index),[sagecrm](http://www.dsdinc.com/products/crm-solutions/index.html),[sage software](http://www.dsdinc.com/products/sage-payment-solutions/index.html),[erp software](http://www.dsdinc.com/products/sage-accpac-erp/index.html)

---

### Post by IcarusR on 2010-11-25
This maybe what you are looking for

[http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt")

---

### Post by Scooter_X on 2010-11-25
Yes, thanks. I did find that list yesterday. I had like 7 options for mine, I've tried a couple with no luck. Gonna' hack away and try the rest soon.

---

### Post by Scooter_X on 2010-11-29
Got it. 

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules]("https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules")

Shoulda' probably just done that from the beginning. The different options I had to plug in for my 'model' didn't even pertain to my laptop. There were 2 'asus' options but both way different models than my 1001pxb. The others were different brands altogether. Didn't try them all. But anyway, this works now.

Edit: mind you, I don't know if the mic works. I don't have a mic to plug in. I probably won't use it.

---

