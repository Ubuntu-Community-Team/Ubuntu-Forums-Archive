---
title: "Does 8.10 and Asus eee 1000he have wifi problems?"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by crispeto on 2009-03-26
My son has an Eee 900 with the celeron processor and I tried to put 8.10 on and it has had nothing but wifi problems. I can't even see my SSID. I read that this model has had issues. I ended up putting on Ubuntu-eee instead. Can anyone tell me if the the 1000he model has the same issues with 8.10? It comes with WinXP but I want to Wubi it to Ubuntu. I'm hoping it works out of the box. Thanks

---

### Post by LiamWilson on 2009-03-26
Well a quick [google search](http://www.google.co.uk/search?q=ubuntu+asus+1000he+wifi&btnG=Search&hl=en&sa=2) revealed this:
[http://ubuntuforums.org/showthread.php?p=6950989](http://ubuntuforums.org/showthread.php?p=6950989)

But I'm not sure if that Will apply to you or not. It might depend how you are installing it. Wubi should set up a dual boot system, anyway, so you can test it out, and then earase your Windows partition if you want to.

---

### Post by sgosnell on 2009-03-26
Wifi works fine on the 900 if you follow [these instructions](https://help.ubuntu.com/community/EeePC/Fixes).  It covers all models of the Eee, so make sure you read it all, and especially the parts specific to your model.  FYI, wireless works out of the box in Jaunty, which has just been released in beta.  I've been running the alphas for some time, and it works very well on the 900, with no tweaks needed.

8.10 requires installing the backports and blacklisting a couple of things, I can't recall the exact names, but it's all detailed on the link I provided.

---

