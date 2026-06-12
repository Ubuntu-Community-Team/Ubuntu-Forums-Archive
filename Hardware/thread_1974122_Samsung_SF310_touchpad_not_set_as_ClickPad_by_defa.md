---
title: "Samsung SF310 touchpad not set as ClickPad by default"
date: 2012-05-05
forum: Hardware
---

### Post by f_padia on 2012-05-05
This is just a heads up to anyone with a Samsung SF310 laptop (or anything similar that uses the same Elantech touchpad). After struggling to use the touchpad properly in 11.10 and trialling many different patches I was very happy to read that 12.04 had better support for clickpads. However, after upgrading I was still finding the clickpad wasnt working correctly, most annoyingly it wouldnt allow me to do 2-finger click and drag movements. Now though I have found the solution and I felt it was important to share!

Basically it turned out that the touchpad wasnt set as a clickpad by default in synclient. I have no idea why this is but it turned out to be the case nonetheless. Anyway to fix it you can either just enter 'synclient ClickPad=1' into the terminal which will work for only the current session. To make it permanent I just made a script (see attachment) and got it to run at startup. Not sure if this is the best way but it works!

I hope this helps anyone else having the same problem as me. 

p.s. in the script there are also a few more parameters set. these are just to enable the edge movement of the touchpad which basically means that if you are (1-finger) dragging something and you reach the edge of the touchpad the curser will keep moving. its quite a handy feature.

---

### Post by toddmeaney on 2012-05-26
This worked great for me! Thanks! The only thing that does not work is the right click on the clickpad. Any thoughts on how to get that to work? 
Thanks!

---

### Post by joum on 2012-12-13
> **toddmeaney said:**
> This worked great for me! Thanks! The only thing that does not work is the right click on the clickpad. Any thoughts on how to get that to work? 
Thanks!

Same here... no right click bugs the hell out of me! And palm detection too...

I read somewhere there was a workaround that allowed to define a certain area of the clickpad as the right-click area, but that it brought more problems than it solved... It was in ArchLinux's forums I think... Not very helpful, and since I'm an übernoob, I won't try it since some people reported being hard to set back to this (incomplete) kind of functioning.

---

