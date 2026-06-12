---
title: "VIA graphics card and laptop screen"
date: 2004-11-04
forum: Hardware &amp; Laptops
---

### Post by Artiom on 2004-11-04
Hi to every one, I'm new to linux so I don't know all the ins and outs.

I installed ubuntu on my laptop (it's not from major manufactor) and all looks great.

But some small things:

1) when I was installing ubuntu, in graphic card section I choose VIA. But after installing->rebooting->starting ubuntu linux...->all other stuff, I can see it on screen->but when it comes to login screen it shows just black screen.
So I installed again with VESA in graphic card section, and it works.

My question is what is the easy way to install VIA driver for my graphic card (VT8623[Apollo CLE266] integrated CastleRock graphics)

2) when I'm closing the screen of the laptop, it turns off (which is ok), but when I opening it back, it shows black screen with promote sign (" _ ") and no response?

---

### Post by cseg on 2004-11-04
I have that graphics chip in my VIA M10000 motherboard ([http://www.mini-itx.com/reviews/nehemiah/](http://www.mini-itx.com/reviews/nehemiah/)). 

I ended up installing X from x.org to get full support for the CLE266.

This post has the script I used to build and install x.org 6.8.1 on Warty:

[list][http://www.ubuntuforums.org/showthread.php?p=9370#post9370](http://www.ubuntuforums.org/showthread.php?p=9370#post9370)[/list]
Perhaps something close to it will work for you.

---

### Post by Artiom on 2004-11-04
I think it's too early in my life as linux user to do such things  ](*,) 

(linux user from 1st November  \\:D//)

---

### Post by Artiom on 2004-11-08
I found answer to my second problem  :lol: 

when you open screen, clicking Alt+F7, then you need to move mouse so (probably screen saver) will go off (in my case you need to enter password) and everything goes back like it was before you closed your screen.  :twisted:

---

