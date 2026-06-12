---
title: "VLC Player flickers when playing a movie"
date: 2008-11-07
forum: General Help
---

### Post by Archimedes0212 on 2008-11-07
Hey All -

I just did a fresh install of Intrepid Ibex.  I installed VLC player to play movies.  When I play them however, the screen continuously flickers.  It is very annoying and I have no idea how to fix it.  It also does the same thing when I try playing the movies in something like Movie Player.  

Any Ideas on how to fix this?

Thanks in advance!

---

### Post by abhiroopb on 2008-11-07
This may be because of compiz. Try turning of compiz...System>Preferences>Appeareance>Visual Effects (Tab)>None

---

### Post by scouser73 on 2008-11-07
> **Archimedes0212 said:**
> Hey All -

I just did a fresh install of Intrepid Ibex.  I installed VLC player to play movies.  When I play them however, the screen continuously flickers.  It is very annoying and I have no idea how to fix it.  It also does the same thing when I try playing the movies in something like Movie Player.  

Any Ideas on how to fix this?

Thanks in advance!

VLC 0.9.4 does have some problem with display; flickering, vision stops but audio continues to play. There is an updated version of VLC but I think that it needs to be compiled.  There have been a few posts about the current version of VLC, so you're not the only one experiencing it.

---

### Post by Archimedes0212 on 2008-11-07
I tried turning compiz off and that did the trick.  However, before I did a clean install, everything was working perfectly fine, compiz and all.  Is there any way to get VLC to work along side of compiz?  Thanks everyone!

---

### Post by Archimedes0212 on 2008-11-07
i've tried a bunch of stuff including resinstalling restricted hardware drivers and reinstalling vlc and compiz.  My movie playback will flicker no matter what with any visual effects above none.  This is really frustrating.  Any thoughts would be very appreciated

---

### Post by Tavish on 2008-11-20
I had the same problem.

In VLC go to Tools > Preferences > Video.

For Output, choose X11 video output.


That is all.  I don't know if this is the best way to do it, but it works well enough for me.

Hope it works out for you!

---

### Post by Archimedes0212 on 2009-01-09
wow, thanks.  It didn't work the first time I did it, so I gave up for a while, but I came back to it today, after several updates and a variety of other things, and that X11 output did the trick

---

### Post by esc1 on 2009-01-11
This thread helped me. Thanks you!

---

### Post by replikanxxl on 2009-01-14
Hey everyone . I donno how these solutions work for you  , but """turning off the visual effects of desktop""" worked for me . Have fun   

Im using Kubuntu 8.1 btw

---

### Post by lorcanf on 2009-02-03
Thanks, I found this problem very annoying. But changing output to video X11 worked perfect

---

### Post by jbraswell on 2009-02-08
> **replikanxxl said:**
> Hey everyone . I donno how these solutions work for you  , but """turning off the visual effects of desktop""" worked for me . Have fun   

Im using Kubuntu 8.1 btw

Me, too.  Thanks!

---

