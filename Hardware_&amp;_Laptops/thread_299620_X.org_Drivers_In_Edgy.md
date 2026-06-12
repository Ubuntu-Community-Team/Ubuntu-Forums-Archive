---
title: "X.org Drivers In Edgy"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by wsmoser2004 on 2006-11-14
I have a laptop with an ATI card, which I've had lots and lots of problems getting to work with fglrx.  I've gotten to the point where I'm tired of struggling with fglrx, and I don't want to ever have to use it again.  ATI no longer supports the card anyway (Mobility Radeon 9200), so fglrx is pretty much out of the question for me.

However, now that I've upgraded to Edgy, I get decent frame rates in glxgears and PlanetPenguin Racer, and I'm NOT using fglrx.  I think the performance is actually BETTER than with fglrx, although the raw frame rate is a little bit lower and some of the textures look strange in PlanetPenguin Racer.

Is this driver...whatever it is I'm using right now...a complete replacement for fglrx?  Does this mean I could now get Beryl and/or XGL/Compiz working without fglrx?  That would be great...but I feel like there must be some catch here I'm not aware of...

---

### Post by wsmoser2004 on 2006-11-14
I was impatient, and answered my own question by installing Beryl.  It works great, except that on the right side of the screen there is a big black bar.  I think the problem might be that I have a widescreen LCD, and Beryl might not be able to handle the widescreen, so it just stuffs everything into what would be the size of a normal screen.  

Has anyone else had this problem?

---

### Post by bonzini on 2006-11-17
Go to the wiki.

Search there for "radeon", then for "CompositeManager/AIGLX".

I've got the 9200 as well and this seems to work just fine.

---

