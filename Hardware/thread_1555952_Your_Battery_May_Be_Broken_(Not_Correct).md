---
title: "Your Battery May Be Broken (Not Correct)"
date: 2010-08-18
forum: Hardware
---

### Post by Martin Marshalek on 2010-08-18
I have a 2 1/2 year old Compaq Presario F730US which I kept hooked to AC power a majority of the time and didn't use on battery power very often. It never had the greatest amount of batter power to begin with and as my situation was, I had given it the perfect conditions for the battery to degrade. I started getting the "Your Battery May Be Broken" notification and started looking more deeply into this. If I open the power statistics window (by clicking on the battery icon in the notification area) It tells me that the battery was designed to hold 88.8 Watt-Hours of power and tells me that it now holds 42.6 Watt-Hours, which would indeed indicate that my batter was failing. I then removed the battery and checked it and it was written that it was 43 Watt-Hour battery, meaning I had only lost ~0.4 Wh of power capacity. To me, this means that whatever daemon is reporting to the statistics of the batter is not reporting correctly. Is there anyway to correct this?

---

### Post by Pogo1 on 2010-08-26
> **Martin Marshalek said:**
> ... I started getting the "Your Battery May Be Broken" notification and started looking more deeply into this... To me, this means that whatever daemon is reporting to the statistics of the batter is not reporting correctly. Is there anyway to correct this?

There is... somewhere. I came across a mention of it in a forum some time back (possibly in a NBR forum). I applied the fix and it worked. I have just reinstalld Ubuntu after a crash, and the same message is back.

I'll keep hunting and post here when I find it.

I just found this thread <https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190>
It didn't fix the problem, but it prompted me to remember that the fix was in gconfig.

I'm still looking....

Cheers;

Pogo.

---

### Post by Pogo1 on 2010-08-26
> **Pogo1 said:**
> There is... somewhere. I came across a mention of it in a forum some time back (possibly in a NBR forum). I applied the fix and it worked. I have just reinstalld Ubuntu after a crash, and the same message is back.

I'll keep hunting and post here when I find it.

I just found this thread <https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190>
It didn't fix the problem, but it prompted me to remember that the fix was in gconfig.

I'm still looking....

Cheers;

Pogo.

...And here it is. <http://linux.aldeby.org/get-rid-of-your-battery-may-be-broken-notification.html>

Now it can't warn you if your battery really is broken, but it won't lie about it until then ;)

---

