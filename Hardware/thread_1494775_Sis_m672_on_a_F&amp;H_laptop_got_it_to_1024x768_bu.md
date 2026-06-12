---
title: "Sis m672 on a F&amp;H laptop got it to 1024x768 but how to get it to 1366x768?"
date: 2010-05-27
forum: Hardware
---

### Post by Hex99 on 2010-05-27
Hi there,
I would say I am a "noob" but after 24 hours hacking away at xorg.conf file I think I qualify as "young but blooded".

I have this Foehn & Hirsch laptop which is pretty great for £299 and comes with no OS. I decided to finally get rid of Windows the hard way...

Anyway, the thing apparently has an Sis m672 chipset for the video and yes, I do know Sis is a "problem" company etc etc I have been lurking on the forums like a maniac and have even tried several Sis 671 drivers, none of which worked.

So far the best solution (which got me to have 1024 x 768 resolution was posted as a xorg.conf file which i copied from the post under one of the reviews of the laptop on the e-buyer web-site (easy to find as there is only one type of F&H laptop)
here: [http://www.ebuyer.com/product/185894/show_product_reviews](http://www.ebuyer.com/product/185894/show_product_reviews)

Now I KNOW this laptop works in 1366 x 768 under windows...so...could one of you Ubuntu wizards PLEASE, pretty please, hack the windows driver of this sis m672 and fix it so that I can see my screen without it stretching everything a bit as it's doing currently?

(i.e. get the proper 1366 x 768 resolution working.)

I would be SO grateful and I would be happy to become an evangelist for Ubuntu if this problem could be fixed as it's the only think preventing me from dumping windows permanently.

Please help you Obi-Wans
(ps I am running ubuntu 10.04 32 bit version)

thanks.
G.

---

### Post by ajgreeny on 2010-05-27
Have a look at [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) as it may help you get the resolution you want by adding the appropriate modeline to your xorg.conf file.

I remember playing around with an old machine with a sis card about 5 yrs ago, and I did get that running, but now have no idea what I did to do so.

---

### Post by Hex99 on 2010-05-27
Thanks for this. I don't know yet if it will work...but it's given me something new to try. 
I do heartily wish though that the Ubuntu community would support the idea of a specific Ubuntu laptop that just works perfectly with any Ubuntu version....straight out of the box without any tweaking. I think it would be such a HUGE impact for people like me who are sick of Windows but are too illiterate to fully move to ubuntu easily. It's sort of like the dark ages and I am an illiterate Pleb. Those who know should package the "religion" into a nice little white box that I can buy and take home and just work on, believing it all works due to Magic and ritual, so I don't have to concern myself with complicated things like "ethics" (the command line) or "morals" (a rough understanding of the processes Linux uses). I will now ritually disembowl an effigee of Microsoft as I pray to the Ubuntu priests that this solution will come soon....

---

