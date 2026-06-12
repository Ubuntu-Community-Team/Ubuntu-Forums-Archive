---
title: "edge graphics worse than dapper, radeon 9000"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by TomFumb on 2006-11-06
Hi, hopefully a quick problem with an easy solution...

I just got rid of xubuntu dapper and installed xubuntu edgy, and the graphics aren't performing as well as they were in dapper. 
In dapper I could quite happily play armagetron (why play anything else?), but now in edgy the graphics just crash out when the game loads. The game is set up the same, and comparing the xorg.conf files from each install there's no obvious difference. I don't know enough about the other X11 config files to mess about with them, so any advice on what I can do to improve performance would be great. Generally the GUI works fine, with no hangs or crashes, it's just this game, and I assume others too

I'm running xubuntu edgy on a thinkpad x22, with a radeon mobility 9000

Any help would be greatly appreciated (vague suggestions would do).

TomFumb

---

### Post by Joe_CoT on 2006-11-06
run:

> glxinfo | grep direct
is it on or not?

---

### Post by TomFumb on 2006-11-07
Thanks Joe-CoT,

:~$ glxinfo | grep direct
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes


I guess that means yes, I'd have thought that this was a good thing? Any ideas?

To be honest, not being able to play a game isn't the worst thing in the world, but it just makes me think that I'm due some more unforseen graphics issues as a result.

---

