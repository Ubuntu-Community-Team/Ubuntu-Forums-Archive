---
title: "Thinkpad X61 (Intel Wireless 3945) suspend."
date: 2008-11-08
forum: Hardware
---

### Post by cookieofdoom on 2008-11-08
So half of this post is me trying to find a solution, half of it is me posting a work-around. Suspend on my Thinkpad X61 is buggy. I've tracked down the bug, I think, to the wireless card. When I suspend and try to come out of suspend, the laptop comes out for about 2 seconds and then goes right back to sleep. Asking the laptop (pressing function, or the power button) to come out of sleep one more time causes the laptop to come out of suspend properly.

Additionally, going into suspend with wireless on while not connected to a network does not work. If I'm not connected to a wireless network (or haven't turned off wireless through networkmanager) the suspend light blinks and blinks and blinks for about 30-45 seconds, and then returns me to the desktop. I have to either connect to a wireless network, or turn off wireless.

I should also point out that suspend worked flawlessly in Hardy (with the exception of issues I had if I took the laptop out of the docking bay without restarting the machine). The fact that turning off wireless seems to help my problem of not going into suspend tells me that the problem is likely related to the wireless card. Additionally, I get an error message occasionally when going into suspend. Something like:

```
wireless event too big 320
```

Anyway, if anyone has any suggestions, they're much appreciated. Hopefully this post might help someone else, too.

---

### Post by cookieofdoom on 2008-11-17
Sorry to double post, but I should point out that this problem does not exist in 64 bit Ubuntu.

---

