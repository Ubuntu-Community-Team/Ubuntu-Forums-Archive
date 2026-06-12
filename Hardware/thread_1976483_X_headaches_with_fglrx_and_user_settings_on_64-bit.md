---
title: "X headaches with fglrx and user settings on 64-bit Ubuntu 12.04"
date: 2012-05-08
forum: Hardware
---

### Post by wbushey on 2012-05-08
I've been spending the afternoon fighting with the AMD proprietary drivers and Ubuntu 12.04. This started off with trying to get my two monitors + tv to work the way I want (two monitors active as an extended desktop, tv off). In the process, I've tried various settings in amdcccle and the Ubuntu's Display dialog, and I've unplugged the tv.

Now the problem is I cannot log in with my user. When I log in with my usual username, X appears to hang. One of the monitors will shut off, the other will be lite black, and my keyboard will be useless. However, the two monitors work well on the log in screen, and if I log in to a guest session. The last thing I recall doing in a successful user session was enable both monitors in amdcccle, and then restarting.

Obviously, there's something weird going on in my user's settings. I have /home on a separate partition that has been used by a Gentoo installation for ~3 years, so I'm sure there's one or two things from that are contributing to this problem, but I'm not sure what those things are or how to fix them.

Here is my current [xorg.conf]("http://www.pastedump.com/paste/2215") and the [Xorg.0.log]("http://www.pastedump.com/paste/2216") of a failed attempt to log in with my user. At a glance of the log I see a lot of repetition of 
```
BUG: ../../dix/getevents.c:850 in scale_to_desktop()
```
followed by a back trace. I wonder what that is all about.

Can anybody suggested what I should do?

Thanks

---

