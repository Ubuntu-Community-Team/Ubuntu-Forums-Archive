---
title: "4 GB ram w/ 32bit Ubuntu"
date: 2009-04-07
forum: Hardware
---

### Post by Lucky75 on 2009-04-07
Hey,

My system currently only shows 2.75 gigs of ram, even though I have 4gb installed. How do I enable it to use all 4?

Thanks!

---

### Post by linuxuser21 on 2009-04-07
Are you sure all the RAM sticks are good?

---

### Post by Cracauer on 2009-04-07
You need two things:

1) A BIOS with working remapping
2) A 32 bit kernel with PAE compiled in (or a 64 bit kernel)

---

### Post by jdong on 2009-04-07
> **Cracauer said:**
> You need two things:

1) A BIOS with working remapping
2) A 32 bit kernel with PAE compiled in (or a 64 bit kernel)

To emphasize on point 2, the linux-server kernel on 32-bit Ubuntu has PAE.

---

### Post by ramjet_1953 on 2009-04-08
To un-geekify the comments of the previous posters, here is a how-to in easily understandable English:

[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

I also believe that the 2.6.24 kernel natively supports PAE.
This is great if it does, as there can be problems with having to re-install drivers for things like your video card and networking if you install the server kernel.

Regards,
Roger ;)

---

### Post by Lucky75 on 2009-04-08
> **ramjet_1953 said:**
> To un-geekify the comments of the previous posters, here is a how-to in easily understandable English:

[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

I also believe that the 2.6.24 kernel natively supports PAE.
This is great if it does, as there can be problems with having to re-install drivers for things like your video card and networking if you install the server kernel.

Regards,
Roger ;)

So...by installing PAE, what does that break? And if the 2.6.24 kernel natively supports PAE, why do I need to install the linux-server packages? 

And I'd rather run a 32bit OS than a 64bit os, because switching to 64bit would probably break a whole lot more I would assume ;)

Thanks for the replies! My mobo is am Asus P5NSLI w/ a Core2Duo E6600, and I'm using the nvidia drivers for a 7600GT gfx card.

> **linuxuser21 said:**
> Are you sure all the RAM sticks are good?

Yeah, no errors on memtest

---

### Post by jdong on 2009-04-08
> **Lucky75 said:**
> So...by installing PAE, what does that break? And if the 2.6.24 kernel natively supports PAE, why do I need to install the linux-server packages? 

No, CONFIG_PAE is turned off for the desktop (generic) kernels; there's still some systems that behave weirdly with it turned on.



> 
And I'd rather run a 32bit OS than a 64bit os, because switching to 64bit would probably break a whole lot more I would assume ;)

Thanks for the replies! My mobo is am Asus P5NSLI w/ a Core2Duo E6600, and I'm using the nvidia drivers for a 7600GT gfx card.



Yeah, no errors on memtest



Now now, I wouldn't be that sure in this day and age that a 64-bit OS is that "broken" compared to a 32-bit OS; I'm running 64-bit Ubuntu on all my systems that support it, without a hitch.

---

### Post by Joeb454 on 2009-04-08
> **jdong said:**
> I'm running 64-bit Ubuntu on all my systems that support it, without a hitch.

This is the same reason I decided to try 64-bit again, I heard it had come a long way, I had 4GB RAM, so I thought "hey why not?"

It works just fine, in fact - I've yet to notice a difference in any of the applications I run :)

---

### Post by Lucky75 on 2009-04-08
Ok, so:

1) If I were t install the server packages, it should be detected after reboot?
2) Should it break anything?
3) If it were to break, how would I go about undoing my changes?

Thanks!

---

### Post by jdong on 2009-04-08
> **Lucky75 said:**
> Ok, so:

1) If I were t install the server packages, it should be detected after reboot?
2) Should it break anything?
3) If it were to break, how would I go about undoing my changes?

Thanks!

It just adds a new kernel option to the list of kernels in GRUB; nothing more. If you select the -generic kernel you bypass anything the -server kernel does.

Uninstalling the -server kernel package will undo its changes.

---

