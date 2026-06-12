---
title: "Unstable Internet Connection - Compaq Presario CQ60"
date: 2010-12-28
forum: Hardware
---

### Post by jeffymarts on 2010-12-28
Hello, I'm having a problem with my Compaq Presario CQ60's internet connection. I have Ubuntu 10.04 installed with all the settings set to the default as I just did a clean install to see if this would remedy the situation. I am able to successfully connect to my router and all the PCs on my network are able to use the internet just fine. Also I'm using the ath5k driver. I'll also note that my laptop was able to connect to the internet last night and earlier on this morning

Whenever I start up Firefox it will load the homepage but any page thereafter I'll only be able to access at the root folder level. I'm not sure if this is correct terminology for this, but what I mean is that I can visit pages such as [www.facebook.com](www.facebook.com) but not [www.facebook.com/about/profiles](www.facebook.com/about/profiles).

I would be more than grateful for any help or advice that can be offered and if others have already been able to solve this problem then I have failed to find the thread and I would like to apologize.

---

### Post by jeffymarts on 2010-12-29
I'm starting to think that this might be a network issue and not a OS issue. What I'm going to do later on is test to see if I can access the Internet through a direct wired connection to my router and I'll also be connecting to another wifi network.

---

### Post by jeffymarts on 2010-12-29
Turns out that it was my router freaking out or a more accurate way to put it would be that my DNS settings were messed up.

---

### Post by natalizi on 2011-01-05
One possible solution is to turn MTU to 1492 (in your router settings). In my case the internet worked perfectly when computer was connected directly to cable, but when using router (wireless or wired) some sites could not be acessed (facebook, bank and newspaper restricted area). MTU was setted to 1500. After changing to 1492, problem solved.

---

