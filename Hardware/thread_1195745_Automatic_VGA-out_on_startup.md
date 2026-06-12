---
title: "Automatic VGA-out on startup"
date: 2009-06-24
forum: Hardware
---

### Post by Dysport on 2009-06-24
I have the following problem: I have a laptop with a broken display connected with a VGA cable to an external monitor. On boot it shows the bios messages and the ubuntu splash screen, but as soon as gnome starts the screen goes black. I always have to press [fn] + [F5] to redirect to the external monitor again.
Although this isn't fatal, it's still annoying me because I mostly use the laptop closed with an external keyboard and mouse (= no fn-key).

Is there a way to get X11 to use the VGA-out port by default? Or maybe a little script that "presses" [fn]+[F5]?


UPDATE: Managed to get it working by editing the xorg.conf. In case someone has a similar problem I'll attach the file.

---

### Post by d3ngar on 2009-07-26
I have a very similar issue...

My *only* monitor is a 37inch flat screen TV. It's not recognised and the standard resolution ubuntu picked by ubuntu (1154x864). And the screen says 'out of range'.

I managed to set the resolution in my profile to 1024  so once I logged in everything is fine. But I still have to type in my login on the blank screen.

Is there a way that I can set the startup resolution to 1024?

Thanks,

Chris

---

### Post by Dysport on 2009-07-27
> **d3ngar said:**
> I have a very similar issue...

My *only* monitor is a 37inch flat screen TV. It's not recognised and the standard resolution ubuntu picked by ubuntu (1154x864). And the screen says 'out of range'.

I managed to set the resolution in my profile to 1024  so once I logged in everything is fine. But I still have to type in my login on the blank screen.

Is there a way that I can set the startup resolution to 1024?

Thanks,

Chris

In which way should your problem be similar to mine?

Have you tried editing the xorg.conf file directly via 'gksu gedit' or 'gksu nano'?

And if it's just the login you might consider timed or autologin, this way you don't have to enter anything.

For the future: You should make your own thread, this way you will get your answer more quickly because more people will read it. It is also needed to keep the information structured for further use.

---

### Post by d3ngar on 2009-07-27
Well, I figured in the way that we'd both like to configure something about our monitor when the login appears.

Maybe you are right and it's not so similar - but, hey, didn't mean to offend you!

I did try editing the xorg.conf, but it's not doing it for me...

---

### Post by Dysport on 2009-07-27
I wasn't offended at all :D Sorry, my fault if you got the wrong impression there.
Would the autologin be an acceptable solution?
Unfortunately I don't know how the xserver handles the login window differently from the normal desktop - as I already suggested, you might want to start a new thread in order to get answers from people who know the architecture of x11 better.
Good luck!

---

### Post by d3ngar on 2009-07-27
Thanks, I will try the new thread... Although I have a fair few threads running at the moment.
My new system and the requirements are a bit 'unusual' :)

No, auto-login isn't quite what I need.

The computer is actually on auto-login, but locks that session. There are various processes that I configured on one user that has a lot of rights. 

Since it's quite a public computer (I use it also to watch TV, DVDs and etc...) and I don't want people to have these rights, the screen locks on auto-login and you can then switch sessions to a 'user' account.

---

