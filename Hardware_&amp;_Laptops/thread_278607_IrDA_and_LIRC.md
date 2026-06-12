---
title: "IrDA and LIRC"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by rgoble on 2006-10-16
I have 6.06 installed on a Dell Inspiron 600m laptop and I am trying to get lirc working so that I can control the laptop with a remote. 

I was able to build lirc-0.8.0 and get it installed. During the setup I told it i was using an IrDA port on COM3. I could then load the lirc_sir module and was able to run irrecord however it would never receive a signal from the remote. It turned out that the IrDA port was disabled in bios so I enabled it and set it to COM3.

When I restarted and tried to modprobe lirc_sir I got the error
```
FATAL: Error inserting lirc_sir (/lib/modules/2.6.15-26-386/misc/lirc_sir.ko): Device or resource busy
```

At this point I did some more searching and found this post
[http://ubuntuforums.org/showthread.php?t=214421&highlight=lirc_sir]("http://ubuntuforums.org/showthread.php?t=214421&highlight=lirc_sir")
and figured I would give it a shot. But as it turns out I don't have the smsc-ircc2 module so it didn't work.

So there is where I am stuck and would like some help on what I need to do next to get it working. If you need any more info or log output let me know and I will post it.

Thanks.

---

### Post by Stewori on 2007-05-30
My Stroy is exactly the same - only on a ThinkPad T30.
First I probed lirc_sir successfully, nothing happened, found out about bios, enabled Infrared,
then got exactly the same Device-busy-Error as descibed above.
Then I had the Idea, this might happen because of another loaded IrDA module.
So I tried to remove the module called irda. Finally it worked by removing all those modules (in my case nsc_ircc), wich depent on irda.
After that, probing lirc_sir did not end up in any Error any more. Unfortunately it ended up in a complete System-Hang-Up instead. The System just freezes. No mouse Movement, no reaction to any key Kombination.

Any ideas?

---

