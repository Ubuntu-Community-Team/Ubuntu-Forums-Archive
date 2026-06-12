---
title: "nVidia GeForce Go 7300 dual-head: Separate X, TwinView, Xinerama"
date: 2008-05-11
forum: Hardware
---

### Post by Xianath on 2008-05-11
Hi all,

I am trying to get a working dual-head setup with the following requirements:

A) Desktop resolutions are different

B) Change desktop resolution on the fly
This is pretty much indispensable since my laptop LCD, work monitor, conf room projector, home monitor and home TV all run different resolutions.

C) Correct input handling between screens
Things like drag-and-drop, global shortcuts (such as the mute button), per-application virtual desktop assignment, etc.

D) Window manager recognizes both screens as such
Maximize should only cover the current screen, I want to have a panel at the top of the lower screen, or if running side-by-side -- I don't want it to span both screens.

E) Shut down one GPU head to conserve power
This is a nice-to-have but not indispensable feature.

I am stuck with an nVidia G72M (this is a Dell Latitude D620) so I need to find a solution for this particular piece of hardware. It's a true dual-head and supports TwinView, however it is not without its own problems. Here's a matrix of what I have been able to get to work so far:


```

                 |   A   |   B  |   C  |   D  |  E
-----------------+-------+------+------+------+-----
Separate Screens |  Yes  |  Yes |  No  |  Yes |  ?
TwinView         |  Yes  |  Yes |  Yes |  No  |  ?
Xinerama         |  Yes  |  No  |  Yes |  Yes |  ?

```


Is there any way to turn any "No" above into a "Yes" that I've missed?

Thanks,
Peter

---

