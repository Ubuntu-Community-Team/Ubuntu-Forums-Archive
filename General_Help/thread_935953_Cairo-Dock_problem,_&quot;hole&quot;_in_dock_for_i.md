---
title: "Cairo-Dock problem, &quot;hole&quot; in dock for inactive windows"
date: 2008-10-02
forum: General Help
---

### Post by DieseL1988 on 2008-10-02
I'm running Cairo-Dock version 1.6.2.3 - which is significant because this only happens in this recent version.

Take a look at my screenshot and you'll see theres a square gap in the dock. This is my Firefox icon which is an "active" icon but an inactive window (I've moved to a different desktop). If I'm actually using the firefox window the icon reappears it's only when I move away to another window it disappears taking a chunk of the dock with it. As soon as I mouse over the dock the icon comes back until the next time I navigate away from the firefox window.

This problem only occurs when specifying a background image for the dock which is using the 3D Plane View. Also if I set the background image to tile the problem goes away, but the background image isn't designed to tile ;)

I've tried changing settings for indicators etc. etc. and nothing seems to have an effect. I've run out of ideas to be honest.

Anyone else having this problem? Anyone know of a solution?

---

### Post by fabounet on 2008-10-02
Seems the dock is considering the icon as a physical separator...
In the config of the 3Dplane view, what happens if you set the separator to the normal one ?
By the way I'm really interested by your background image, could you please send it to me ? :-) (fabounet -at- users . berlios . de)

---

### Post by DieseL1988 on 2008-10-02
Changing the separator doesn't seem to do anything, and it's not quite the same as a physical separator, the area that disappears is square-ish and covers only the area for the icon and it's reflection, the indicator is left alone.

EDIT: Wallpaper - [http://mac-ray.deviantart.com/art/Wooden-Floor-New-v2-96816978](http://mac-ray.deviantart.com/art/Wooden-Floor-New-v2-96816978)

---

### Post by DieseL1988 on 2008-10-03
Anybody even looked in to this? There must be others out there using Cairo-Dock and experiencing this problem? I have got it on two different PCs, one is even a fresh install!!

M.

---

### Post by benoit2600 on 2008-10-03
Are you trying with another theme ?

can you send me your theme by mp ?

---

### Post by DieseL1988 on 2008-10-03
It happens no matter what theme, I've got it on two different machines... one is using a different background etc. :(

---

### Post by fabounet on 2008-10-06
maybe I've found something.
I think it should work with the default view or the curve view.

by the way I was talking about your dock's background :-)
I'd like to make a theme with it.

---

### Post by DieseL1988 on 2008-10-06
I'm running in default view now, which is a shame because the 3D view was very nice with reflections etc. 

The dock background is :-

[http://nardoxic.deviantart.com/art/AluCurved3d-port-for-OD-92107891](http://nardoxic.deviantart.com/art/AluCurved3d-port-for-OD-92107891)

---

### Post by fabounet on 2008-10-07
thanks for the background !
and be delighted, since I've fixed the problem ^_^

---

### Post by DieseL1988 on 2008-10-07
Well not really, we've concluded that the problem doesn't occur in the curve or default views. I still can't use the 3D plane view with a background :(

---

### Post by fabounet on 2008-10-07
yep, it's on the SVN.
if you don't use it, it will be available in the coming soon 1.6.3

---

