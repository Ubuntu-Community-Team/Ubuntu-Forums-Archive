---
title: "start rhythmbox playing and hidden, fractional second sleep, and strange black window"
date: 2008-09-18
forum: General Help
---

### Post by hwttdz on 2008-09-18
I'm trying to start rhythmbox both minimized/hidden and playing music.  I have so far been unable to do this.  

rhythmbox-client --play --hide 
does not work

rhythmbox-client
sleep 1
rhythmbox-client --play --hide
works but leaves the screen maximized for a full second, I know I'm being picky, but as far as I see there's no reason why I shouldn't be able to start it both hidden and playing music

The bizarre one:
rhythmbox-client
sleep 0.5
rhythmbox-client --play --hide
This works ... every other time.  So it works the first, the second time, an unnamed window with no contents other than black opens, and it stays open for while, then it closes at the same time as rhythmbox exits.  

If someone knows a way to accomplish my original goal or what this black box is and how to make it go away or how to accomplish sleep for a fraction of a second please share.  Thanks.

---

