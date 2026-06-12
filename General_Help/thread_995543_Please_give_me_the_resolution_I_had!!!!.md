---
title: "Please give me the resolution I had!!!!"
date: 2008-11-27
forum: General Help
---

### Post by arnabdatta on 2008-11-27
I'm using ubuntu from version 6.06. And from then I loved it very very much. A strong reason was that ubuntu is the only linux distro that gave me screen resolution 1152X864(it's also my Windows default resolution). Till Ubuntu 8.04 I was getting 1152X846. But after I installed Ubuntu 8.10 I get highest resolution 1024X768.:(:(:(:(:(:( I've searched forum and done everything that I can. Please help me!! how can I get the resolution I had...

My hardware Conf
Intel Pentium D 3.0GHz
Intel G965RY
1GB DDR RAM

---

### Post by rshnike on 2008-11-27
In screen resolution, does it list your monitor's manufacturer and model or does it have a generic model?

---

### Post by arnabdatta on 2008-11-27
Yeas it's showing SAMSUNG 14".
But I've Samtron 15" Monitor..!!!

---

### Post by CobaltSS on 2008-11-27
What video card do you have? I've briefly tried 8.10 and reverted back to 8.04. If you have an ATI card you may need to install the ATI 8.9 catalyst drivers. ATI 8.10 and newer does not support some older cards anymore eg. radeon mobility 9700 (my card) because Ubuntu 8.10 the Xorg.conf file does not support fglrx by default. So you will not get a restricted driver update. 
long story short try the ATI 8.9 Catalyst drivers then change your resolution in 
Applications > Accessories > ATI Catalyst Control Center
You may also probably need to use the older Xorg.conf to support fglrx.

---

### Post by arnabdatta on 2008-11-27
I've mentioned in my post that I have Intel G965 onboard graphics...

---

### Post by CobaltSS on 2008-11-27
ah, sorry bout that not used to the names of onboard cards because i don't like them at all. well hopefully someone with an ATI card will pass by this thread so my time to write that wasn't a total loss. lol.

---

