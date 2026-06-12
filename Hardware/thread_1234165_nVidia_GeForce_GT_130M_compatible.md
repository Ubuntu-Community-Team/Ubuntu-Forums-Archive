---
title: "nVidia GeForce GT 130M compatible?"
date: 2009-08-07
forum: Hardware
---

### Post by Gitri043 on 2009-08-07
Hi! 
i was wondering if nVidia GeForce GT 130M is compatible with linux? 
 
thanks

---

### Post by tuco penguin on 2009-08-14
Really wanting to buy a laptop with this card in it (Acer Aspire 5739G), I have been trying hard to determine the same thing.  I am still not sure.  Without hardware in hand its hard to tell, and I'm hesitant to buy the hardware without knowing the answer...  Here is what I can say as of 8/14/09:

1.  NVIDIA does not offer Linux drivers (32 bit or 64 bit) on their website, not even beta versions.  I have found no information as to whether they ever will be offered, or when.

2.  There are a number of complaints about a "six-screens" problem when running GT 100M-series NVIDIA GPUs in Ubuntu with the pre-packaged driver.  However, at least one person (see this post: [http://ubuntuforums.org/showpost.php?p=7410442&postcount=10](http://ubuntuforums.org/showpost.php?p=7410442&postcount=10)) found that the nvidia restricted drivers actually did work with his GT **105M **GPU, but that the settings had to be controlled from an nvidia app. rather than from the typical Ubuntu screen resolution menu.  I can imagine this is rather confusing and might lead some to think their card is not working.  I wonder if this rather minor issue with user interface is actually to blame in more cases?  I imagine the GT 105M and 130M are not too different.

3.  It appears that the GT 130M is the same as nvidia's 9600M GT, but produced with a finer resolution fabrication method.  This, too, would lead me to believe the drivers should be readily available.

This is a pretty new GPU, but being used in a number of name-brand laptops which should get distributed widely:  Lenovo, Acer, others.  Linux support can't be that far off, can it?

---

### Post by tuco penguin on 2009-08-16
For anyone still following the thread, a solution to the 6-screens problem with the GT 130M on the Acer 5739G seems to have been found. In xorg.conf, set"ModeValidation" to "NoTotalSizeCheck" See this thread over at nvnews:

[http://www.nvnews.net/vbulletin/showthread.php?t=137379](http://www.nvnews.net/vbulletin/showthread.php?t=137379)

Hope this helps someone.

---

### Post by teflashfire on 2009-08-17
Great solution! Worked pretty well for me! But now my 3d desktop effects are disable. Frankly, I can live with that miniscule failure of the driver, but I was just wondering if there's anything else to be done?

---

### Post by tuco penguin on 2009-08-18
Hardware accelerated graphics and no desktop effects?  Whats the point?

The alternate suggestion in that thread is to alter an offensive modeline to have legal values, I think (something where end of scan is < total number of scan lines, or something like that, if I recall correctly.)  Or try asking over at the nvnews forums.  I assume you already tried re-enabling desktop effects and got the "driver not capable" kind of error.

---

### Post by teflashfire on 2009-08-18
Of course, the loss of desktop effects does bite a little bit... but there is a huge difference in 2D performance versus the generic drivers. I was getting tired of the excessive clipping and frame skipping from doing something as simple as watching a DVD.

---

### Post by tuco penguin on 2009-08-18
Thanks for sharing your experience.  I'm about to purchase a laptop myself--hence my interest.  Which laptop make/model are you using?

---

### Post by teflashfire on 2009-08-20
I'm using an Acer Aspire 5739.

Don't let the lack of a proper driver from Nvidia not yet being out there dissuade you from buying this model of laptop, though. The price point on it is great (under $800 USD), and I get some amazing performance out of this thing. Nvidia will inevitably release a good driver for it, as they almost always provide proper Linux support given enough time.

And the laptop itself is a solid machine. Large, decent processor, 1 GB on board video card, etc etc. Good stuff for the price.

---

### Post by tuco penguin on 2009-08-20
Glad to hear it.  You confirm all my thoughts about this laptop.  I ordered one two days ago... it should arrive tomorrow!  Can't wait.

---

### Post by teflashfire on 2009-08-21
And as I mentioned, use the fix linked to above to get the nvidia driver working (at least partially). Have fun with your laptop! I'm certainly enjoying mine.

---

### Post by tuco penguin on 2009-08-22
I tried this and it seems like desktop effects are enabled just fine!  I don't have the compiz settings manager installed yet, so I can't play with all the fun stuff, but so far so good...

---

### Post by vnluser on 2009-10-03
> **teflashfire said:**
> Great solution! Worked pretty well for me! But now my 3d desktop effects are disable. Frankly, I can live with that miniscule failure of the driver, but I was just wondering if there's anything else to be done?
can you still play some 3d games like Open Arena, TORC...?

---

### Post by adroitster on 2009-10-10
Hello I followed the instructions here and the links on this forum and got everything working including the 3d effects . This was done around 2 months back but today I just tried to use the normal mode in appearance settings but now the problem is that it won't enable the effects again!! It says desktop effects could not be enabled!!! :( please help me in enabling it .

---

