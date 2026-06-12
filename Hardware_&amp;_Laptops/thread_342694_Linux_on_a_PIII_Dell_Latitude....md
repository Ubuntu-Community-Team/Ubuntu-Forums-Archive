---
title: "Linux on a PIII Dell Latitude..."
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by Insomniac20k on 2007-01-20
Hey guys,

My girlfriend needs a new laptop for school and she found a Pentium 3 M Dell Latitude with no operating system. I figured this would be a great time to introduce her to Linux, since Win2000 is quickly losing support and there's no way this thing is gonna run XP. I've already got her excited about how highly customizable Gnome is and she's willing to give it a go.

My question is, would the latest Ubuntu run smoothly on this laptop? It's a 1.2 gig processor with 250 mb of ram. I know the P3's were a high point for intel and the new M's are based off it, so I'm pretty sure it'll work but I figured I'd ask some more knowledgeable people before I give her the go ahead to buy it.

Thanks guys. -Matt

---

### Post by RandomJoe on 2007-01-20
You shouldn't have any trouble.  I have installed all flavors of Linux on a whole mess of Dells in that range.  Just last night I installed Ubuntu 6.06 on a P3-M 1.2GHz or so.  (Latitude C400.)  Works fine.

If she is going to get into any heavier use - lots of browser tabs, multiple apps open, etc - it might be nice to up the memory to 512MB, but I've done fine with 256MB too.

---

### Post by David Corrales on 2007-01-20
I'll add myself to the "buy more ram suggestion". Ebay it for cheap prices :)

---

### Post by james.wilde on 2007-01-20
Another thing, if it's a Latitude.  The TFT screen is apparently limited to 1024x780 although the laptop will push 1280x1024 out of the video port on the back and via a docking station.  This has been a problem for me since I really need 1280x1024 to connect to my machines at work.

Out of the box, Edgy configures the Dell for a max of 1024x768.  However, if you connect your girlfriend's Dell to a screen, you can add 1280x1024 to each line of the colour depth in xorg.conf.  Warning, though.  The machine will not show anything on its TFT screen if you choose this resolution.  You have to change back to 1024x768 before disconnecting.

I'm working on this in another thread.

//James

---

### Post by Insomniac20k on 2007-01-20
Well I doubt the resolutions gonna be an issue. Thanks for the feedback.

I'll have her pickup more ram when she gets the wireless card.

---

