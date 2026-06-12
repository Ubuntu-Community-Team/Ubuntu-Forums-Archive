---
title: "Atheros AR928x not working"
date: 2009-09-04
forum: Hardware
---

### Post by DevinMcElheran on 2009-09-04
I have an HP, it's brand new. I installed Ubuntu 9.04, and it wasn't connecting, it would try and fail repeatedly. So I tried the ndiswrapper fix, now my wireless card doesn't even show up. I uninstalled the .inf driver file for ndiswrapper, and it still hasn't showed up. Now I'm clueless as to what to do. My only connection is wireless, so you can see my problem. Any and all help is much appreciated. Thanks.

---

### Post by DevinMcElheran on 2009-09-05
Bump

---

### Post by DevinMcElheran on 2009-09-07
Solved it, it was just network-manager being wimpy, as soon as I installed wicd it was fine.

---

### Post by NoXiS on 2009-09-07
You know, when I saw this just now I thought the same thing, "Just stick 'Wicd' on and try it." - well, after I stopped screaming "ndiswrapper, nnnooooooo!".

To be honest the KDE network manager does fine in my desktop (which doesn't have wireless), but my laptop with an Atheros wireless card has Wicd set up and it runs like an absolute champ.

Glad you got it sorted already.

---

### Post by DevinMcElheran on 2009-09-22
So I switched to 64 bit the other day, and now, even with wicd, it just doesn't want to go, but now thinking on it, I think I used a 32 bit wicd version, would that make a difference? I did this forgetting that my installation was now 64 bit and not 32, which will take a bit of getting used to concidering my windows 64 does run 32 bit apps. But it kicked the bucket on me a little back, I had to reinstall it and that's when I decided to switch to jaunty 64 bit.

---

