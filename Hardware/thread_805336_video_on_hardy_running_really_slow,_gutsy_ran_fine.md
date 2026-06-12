---
title: "video on hardy running really slow, gutsy ran fine"
date: 2008-05-23
forum: Hardware
---

### Post by himynameiskevin on 2008-05-23
It seems to be a problem with the video drivers.. Anything that involves scrolling lags like nothing I've ever seen. I'm using a Dell Vostro 1000 w/ an ATI Xpress 1150 integrated video card and the restricted ATI drivers that came with Hardy. The diagonal tearing is going the opposite direction as before, and it's much more noticeable. Gmail will hardly scroll at all, it's really frustrating.

I did a clean install, not an upgrade, and the computer is setup exactly as before with XGL, compiz, and the ATI drivers.

Any thoughts? Anyone else sharing the same problem? I did a quick search but nothing came up, sorry if this is a double post.

---

### Post by pcolamar on 2008-05-24
Just the same here with a raden x1600.
Reading some other post seems to be a problem Hardy<>Xgl.
Somebody suggests to remove  Compiz , but I need it .

I have not found a fitting solution yet .

Good luck to both of us.

Palmer

---

### Post by pcolamar on 2008-05-24
himynameiskevin,
  just got the solution.

If you do not need the xgl server (compiz does not need it any longer to run) just follow the instruction here
[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-04/msg02806.html]("http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-04/msg02806.html")

It is working perfectly for me

Cheers

Palmer

---

### Post by himynameiskevin on 2008-06-18
Whoops, forgot to check back on this thread until now. I found a solution after getting frustrated enough, here:

[https://wiki.ubuntu.com/X/RadeonXpress](https://wiki.ubuntu.com/X/RadeonXpress)

Thanks for helping though, I'm not sure if this is a different solution than the one you posted. This got Compiz working using AIGLX, which I didn't even think was possible.

---

