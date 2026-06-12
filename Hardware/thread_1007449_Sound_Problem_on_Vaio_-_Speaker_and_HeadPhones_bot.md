---
title: "Sound Problem on Vaio - Speaker and HeadPhones both on"
date: 2008-12-10
forum: Hardware
---

### Post by nightcrawl on 2008-12-10
I've seen some identical problems but no solutions. So I decide to restart the problem.

I've got an Sony Vaio VGN-SR19VN and **the sound does make his way out from speaker AND (&) from the HeadPhones** :confused:

No, it's not a internal hardware problem because it works simply fine in W. Vista. I even did'nt know that this was a OS function but apparently is. I've got Ubuntu 8.10 and up to date.

So... anyone wants to share a solution? Because it's really annoying not to listen music in work...

---

### Post by nightcrawl on 2008-12-10
Anyone? :(

---

### Post by koenigjm on 2008-12-10
I am having the same issue on my Ideapad Y730.  So at least you are not alone.  ;)

That said, have you seen this?

[http://ubuntuforums.org/showthread.php?t=806620&highlight=lenovo](http://ubuntuforums.org/showthread.php?t=806620&highlight=lenovo)

---

### Post by nightcrawl on 2008-12-11
Ok, tks!

I've got my problem solved with adding the line:

options snd-hda-intel model=sony-assamd

in the file:

sudo gvim /etc/modprobe.d/alsa-base

But with your link (sorry for my bad search), I've been able to add:

 options snd-hda-intel model=hippo 

instead. The difference is that "hippo" add a control volume for the headphones in the AlsaMixer. 

So, **this** problem is solved.

I said "this" problem, because a new one came up with this mess...

My keyboard control volume:

Fn+F2; Fn+F3; Fn+4;

have lost their function. When I press thos keys, I can see in the alsa-mixer that they're controlling the "line in" instead the volume control. :\


Why can't this be simple..... :mad:

Anyone??

---

