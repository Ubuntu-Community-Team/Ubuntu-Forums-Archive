---
title: "Asus Eee 1000HE Wifi Issues"
date: 2009-06-16
forum: Hardware
---

### Post by TheStagesmith on 2009-06-16
(posted this before in the general forum, never got any responses >.<)

So, I've got Ubuntu 9.04 Netbook Remix running on an Asus Eee PC 1000HE. Pretty much everything works great; my main problem is with the wifi.

The wifi works after a boot, but out of a suspend, it simply can't connect. It detects the networks and begins connecting, but never finishes.

I installed [FONT="Lucida Console"]linux-backport-modules-jaunty[/FONT] to see if it would help (as has been suggested to others in other places), but it didn't. 

Any help? I would really rather not have to reboot the dang thing every time I need to reconnect.

---

### Post by Chronon on 2009-06-17
I only occasionally have this problem, but I have found I can usually fix it by suspending and waking again.  Maybe the same is true for you.

---

### Post by TheStagesmith on 2009-06-17
Thanks, though for me this hasn't worked. It ends up refusing to connect to anything without a complete reboot. 

Thanks for the advice though; it seems that a lot of 1000 series owners are having wifi issues. I wonder if it's a driver problem, or if there's something else that we're missing?

---

### Post by cjruppel on 2009-06-29
I had the exact same problem.  The solution in the link below fixed it for me:

[http://www.nabble.com/Re%3A-Wireless-breaks-after-suspend-on-asus-eee-pc-1000HE-p23251447.html](http://www.nabble.com/Re%3A-Wireless-breaks-after-suspend-on-asus-eee-pc-1000HE-p23251447.html)

---

