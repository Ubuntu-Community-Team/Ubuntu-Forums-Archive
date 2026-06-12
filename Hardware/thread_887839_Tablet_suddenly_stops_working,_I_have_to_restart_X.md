---
title: "Tablet suddenly stops working, I have to restart X"
date: 2008-08-12
forum: Hardware
---

### Post by Cherry Cotton on 2008-08-12
This is very strange and has been happening to me for a while. Sometimes, in the middle of using Ubuntu, the stylus on my tablet PC will stop working and I'll have to restart X. After that, all is fine.

Today, this problem returned, so I started looking into it. I found that the "wacom" driver was unloaded... so, I used "modprobe wacom" to bring it back. Still no luck, though.

I tried using "wacdump /dev/ttyS0" to see if the computer is detecting input from the stylus at all. Turns out it is... sort of. If I use this command and then do nothing, I'll get this output:

```
11:27:27.291 WARN: Discarding 98
11:27:27.319 WARN: Discarding 98
11:27:27.351 WARN: Discarding 98
11:27:27.419 WARN: Discarding 98
11:27:27.419 WARN: Discarding A1
11:27:27.419 WARN: Discarding ED
11:27:27.419 WARN: Discarding 00
11:27:27.419 WARN: Discarding 21
11:27:27.419 WARN: Discarding C0
11:27:27.999 WARN: Discarding 98
WacomOpenTablet: Connection timed out
```

However, if I use that command and then wave my stylus in front of the screen, I'll get a cavalcade of those "WARN: Discarding" messages. I can keep the output going for as long as I want as long as I keep moving my stylus in front of the screen. But, if I move the stylus away from the screen, those messages will slow before coming to a stop with a "Connection timed out" message.

How strange!

What's heartening is that if I try "xxd /dev/ttyS0", I'll get output you'd expect, reacting to whether or not and how I'm moving my stylus in front of the screen. Similarly, "sudo cat /dev/ttyS0" behaves as expected, giving me nothing when I'm not doing anything with the stylus, and spewing garbage when I move it close to the screen.

I guess I'm wondering if anyone knows more about this problem, and if anyone has any tips on things I might do to bring the stylus back without restarting X. I wouldn't want to file a bug (I wouldn't even know which project to file a bug with!) until I know more, if that's possible. Thanks!

---

