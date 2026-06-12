---
title: "[SOLVED] Mouse event &amp;quot;queueing&amp;quot;?"
date: 2008-09-09
forum: General Help
---

### Post by Dudman on 2008-09-09
Hello!

In my last thread i diagnosed my problem wrong, so i'll attempt to remedy that and post my real problem here.

It appears that when i send a whole bunch of scroll events via up/down arrow key or mouse scroll wheel fast, it will "queue" them up and keep going even after i have let go of the key.

This doesnt happen on some of my other computers, which are mainly windblows, though some people i asked dont have this same problem.. they just scroll and then stop when you let up on the scrollbar.

I don't think it's the mouse, since i tried a few other mice and all of them had the same problem. Also, i tried a few different apps and they had the same problem, though firefox and epiphany had the most trouble with this.

Is there a way to disable this, or something to make it not 'queue'?

Thank you very much!

-Dudman

---

### Post by Shazaam on 2008-09-09
Reminds me of my ancient Compaq laptop. The only thing that comes to mind is the amount of video and main memory you have installed and if it is "shared" memory. The processor speed might be related too.

---

### Post by Dudman on 2008-09-09
Um.. not sure how much VRam i have, i have an intel 82845G[Brookdale-G] card.
EDIT: From Xorg.0.log i have 131072KB 

CPU is P4 2.3GHz, and i have 512MB of RAM

Don't really know if this would cause the problem or what..

-Dudman

---

### Post by Shazaam on 2008-09-09
"i have an intel 82845G[Brookdale-G] card"
Onboard video card which means "shared memory". So your 512mb of memory is shared at a minimum of 16mb with your main memory (unknown maximum). I know how to change the amount in Windows but not linux.
Also, search the forums for Intel video drivers setup. Might improve the situation.

---

### Post by Dudman on 2008-09-09
Hmm.. so you think getting more video ram would fix my problem...?

Alright, i'll try to allocate some more.

-Dudman

---

### Post by Dudman on 2008-09-10
Bump - attempting to save thread from page 2 monster :mad:

Any ideas other than getting more ram? 

Thanks.

-Dudman

---

### Post by Shazaam on 2008-09-10
Still looking and I found this....
[http://kb.mozillazine.org/Scrolling_is_slow](http://kb.mozillazine.org/Scrolling_is_slow)

---

### Post by Dudman on 2008-09-10
Shazaam: Thanks very much. Turning off compiz fixed this.

Ty :)

-DM

---

### Post by Shazaam on 2008-09-10
Too bad you had to do that but I'm glad that it helped.

---

