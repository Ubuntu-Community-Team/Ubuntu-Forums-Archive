---
title: "I discovered something wierd about AWN"
date: 2008-07-26
forum: General Help
---

### Post by LeoSolaris on 2008-07-26
I just discovered that (the bzr version of) AWN's manager causes a small glitch at start up. Apparently if you check the "Start AWN at login" option in the manager, and have it listed under start up programs in Sessions, it causes some sort of conflict.

I haven't been able to pin down exactly what conflict, but I learned that if you uncheck it in the Sessions, and leave it checked in AWN's manager, it will still start up, and slightly faster. It will do likewise if you leave it checked in Sessions and unchecked in AWN's manager, it just brings up a different momentary white blocks. For me, the Manager checked, Sessions unchecked makes the smallest white block.

Aparently the conflict was causing a little havoc with compiz's bordering, and conky. Before changing this, conky would have a shadow and float above everything randomly if I set it to start at login, even with a script to delay it 10 seconds while everything else loaded. It didn't always get the floating shadow bug at every login, but it was more than half the time. After I made that small alteration to AWN conky started behaving normally.

I had this same issue with the AWN from the repo's so I suspect that this fix would work for anyone else experiencing this issue.

It worked on a Dell Inspiron 1520 with an nVidia GeForce 8400 GS. 

Hopefully this strange fix helps someone else.

Leo

Edit: Alright... after a few restarts and a little tweaking, I have learned that it only helps the floating shadowed conky bug if I set the script to delay conky's start for 10 seconds. That is an improvement over previous attempts to make the conky error go away by delaying it's start up on login... it actually works.

(woohoo   I think that solves all of my minor bugs for the moment. I now have work arounds that do not require me to actually do anything to get them to function.)

---

### Post by xrockislife3016x on 2008-07-26
cool im prolly not even gonna mess around with awn cause i could care less how i launch my apps... good find and fix though

---

