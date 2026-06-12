---
title: "More Inspron 6000 stuff -- multihead ?"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by rearden-steel on 2005-11-15
Hey folks,

Have a Dell Inspiron 6000, had XP, just installed breezy.  Most everything worked out-of-box, which was nice!

However, under XP, when I had a CRT plugged into the back of my box, I could do a multihead with the onboard ATI radeon "mobility" very easily by checking "extend my Windows desktop onto this monitor." One display was the laptop's LCD, the other was the CRT.

This was one of my favourite features of my machine -- I could keep spreadsheets open while reading articles and doing LaTeX stuff (yes, in Windows, I know, I know . . .), it was very slick. 

Now, though, I can't seem to reproduce this.  I set up /etc/X11/xorg.conf to do Xinerama -- two "monitors," two "screens," one "RightOf" the other . . . but any change I make, it seems as if X isn't reading xorg.conf *at all,* it just tries to do 1280x800 on my CRT, and it looks stretched out and horrible.

Has anyone been able to do a multihead with the Inspiron 6000 -- or does anybody have any idea how else it might be done?

---

### Post by rearden-steel on 2005-11-16
Sorry, just read what I wrote and found it wasn't clear.

X starts fine with multihead doing "startx" in runlevel 3, but tries to do native laptop resolution *on the CRT* -- ignoring the panel -- on boot.

What the hell?  /etc/X11/xorg.conf has to be right, why isn't it getting read on boot?  

/var/log/X<tab>  shows RADEON(0) reads primary display as the panel . . . plugged into the port on the *outside* of the box?  after tying to load X on boot

Selfsame log looks good doing "startx" from 3.

What goes on with this damned hippie linux?

---

