---
title: "Inserting DVD Hangs System"
date: 2011-02-15
forum: Hardware
---

### Post by gaelfx on 2011-02-15
I recently updated from 10.04 (64-bit) because my DVD drive wasn't working. I would insert a DVD and almost immediately the system would become unresponsive, e.g. I could move the mouse around, but response to clicks was delayed by at least 1~2 minutes. No matter how long I waited, the system would continue to lag in an unusable manner AND the DVD would never show up in any usable way.

So I decided to try out 10.10 (64-bit) by making a liveUSB with unetbootin to see if the newer kernel and whatnot would actually fix my issues. When I booted up the liveUSB and inserted a DVD, it behaved exactly as it should; after a few seconds, my DVD showed up on the desktop. So I installed, and after installing, the DVD fails in exactly the same way it did in 10.04 and I'm stuck, once again, with a nice, expensive cup-holder. 

I am not the savviest user, but I can use Terminal etc., so what I really need is help with diagnosing the problem, i.e. figuring out why the drive works in liveUSB but not the install, and if possible, help in finding a solution.

---

### Post by sanderd17 on 2011-02-15
When it gets stuck, can you press CTRL+ALT+F1, then you should come in a terminal in which you can login.

after login, run the command
```

top

```
to see what is using all your cpu. then kill it with the 
```

killall

```

You can go back to your graphical environment with CTRL+ALT+F7

can you tell us what process is hanging?

---

### Post by gaelfx on 2011-02-15
I did what you asked, but I wasn't able to login until the system stopped hanging, so when I did used top, all I saw was Transmission, which can't be the problem. After I went back to the GUI, there was an error message saying that the DVD couldn't be mounted, so I mounted it by hand and was able to play it back, but that means that to watch a DVD, I have to deal with a ridiculously unresponsive system as well as waiting for 10-15 minutes before it can actually start playing. Any other ideas?

---

