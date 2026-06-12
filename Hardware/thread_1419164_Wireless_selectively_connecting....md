---
title: "Wireless selectively connecting..."
date: 2010-03-01
forum: Hardware
---

### Post by iwil on 2010-03-01
Hello there, 

Have a question regarding wireless networking... Sometimes the wireless connection does not come back after sleep, reboot seems to let it come back though. I'm guessing that '/etc/init.d/networking restart' should resolve this, or maybe an ifdown/ifup on the wlan0 interface, but to be honest I haven't tried those yet.

I suppose my question is... is there an 'Ubuntu' way to reset the wireless network interface when it disappears? Right clicking on the dock item shows the 'Disable wireless' option grayed out from what I understand.

It's an Atheros chip if that matters at all.


*** forgive me, I'm a long time UNIX user so I can get around fairly well but all these control panels and stuff are new to me. I am not an Ubuntu user, I just have a friend that was having Windows issues so we 'fixed' it with some kubuntu. Since this is on a friends laptop I haven't been there to catch this issue yet but would ideally like to let her know whatever the proper way to deal with this is.

---

### Post by mikewhatever on 2010-03-01
I am not aware of any 'Ubuntu way' to reset wireless. Ubuntu is not all that different from other members of the Debian family, and, I think, control panels and stuff are KDE4 features.

---

### Post by iwil on 2010-03-01
Thanks for your reply.

I'll go ahead and have her restart the networking init script then, looking at it seems like it should do the trick just fine.

Sorry for the dumb question, I come from a Solaris and FreeBSD background and only use X when absolutely necessary so my mentality is in the terminal. I know Ubuntu focuses on using the gui stuff as much as possible so I figured there was some handy network repair utility or something. 

Thanks!

---

