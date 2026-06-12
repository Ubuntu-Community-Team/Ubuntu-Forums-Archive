---
title: "full laptop batterty critically low"
date: 2011-04-04
forum: Hardware
---

### Post by twtduck.ii on 2011-04-04
I just installed ubuntu 10.10 32-bit onto my new laptop (I had it on my old desktop PC) and the battery holds about 1 1/2 hours of charge on windows 7. When I unplug it on ubuntu, it says:

Laptop battery critically low
Computer will hybernate very soon unless it is plugged in.

Also, an alert box appears in the corner saying:

[B]Battery Discharging
[/B]0:03 of battery power remaining (100%)

How can I fix this bug?
Thanks in advance,
Twtduck.ii

---

### Post by Marcelush on 2011-04-05
This is an error from your operating sistem! He can't detect your battery. I don't know how to explain , but if you take your laptop to a specialist he would tell you that i'm right.

---

### Post by kmullins on 2011-04-05
It might be a problem with the APCI if it's a newer laptop. I'd Google around for a bit with your laptop model and try to see if anyone else has had the same problem.

If you want to try to get some more help here, it might be helpful to post some more information like the Laptop Make/Model.

Good luck!

---

### Post by javajames97 on 2011-07-21
i am very sorry that you have not had you query answered to a reasonable extent any earlier, here is the solution (if you haven't already found it)

enter this in your terminal command line
```
gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false
```

this is a very common bug with GDM that it can't predict the remaining time very well

if this doesn't help, post the question to stack overflow, they will be able to talk you through the possible hard ware problems

original source: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/572541/]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/572541/")

---

### Post by twtduck.ii on 2011-07-24
Thanks! Finally, the last of the 5-10 bugs in natty I've worked out (i think). Yay! :D

---

