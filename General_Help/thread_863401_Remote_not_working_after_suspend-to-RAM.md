---
title: "Remote not working after suspend-to-RAM"
date: 2008-07-18
forum: General Help
---

### Post by sebrock on 2008-07-18
I have a iMON PAD working in mythbuntu. Everything works just fine except one thing. Whenever I suspend-to-RAM and wake up again the remote stops working within the frontend. It still works outside, using 'irw' gives output and everything.

So my guess is that mythfrontend is somehow loosing its connection to LIRC. The only way to get the functionality back is to restart the frontend. But that whole procedure kinda takes the point from quick suspend/wake away.

As of now I have to unload the lirc modules at suspend and reload them upon wake up or it wont work at all (and syslog gets flooded by error messages).

Any suggestions on how to make this work?

---

