---
title: "[SOLVED] Dazed and confused kernel message"
date: 2008-11-01
forum: Hardware
---

### Post by ewinslow on 2008-11-01
My system (Dell Inspiron 6000) has been freezing since this mid-summer. It has done it with 8.04 and now 8.10. I thought it was my hard-drive from earlier messages, but with a new hard drive we're getting the same behavior.

I suspect my motherboard is shot. Time for a new machine?

```

Nov  1 00:52:13 ubuntu kernel: [  613.633828] Uhhuh. NMI received for unknown reason a1 on CPU 0.
Nov  1 00:52:13 ubuntu kernel: [  613.633840] You have some hardware problem, likely on the PCI bus.
Nov  1 00:52:13 ubuntu kernel: [  613.633843] Dazed and confused, but trying to continue

```

---

### Post by rrwright on 2008-11-02
I've had this same problem for a few months now, without a solution in sight. It's running on a Dell server and they have replaced the whole thing twice without fixing this. It's an amd64 dual core if that matters.

---

### Post by ewinslow on 2008-11-02
I did run the memtest on my machine and that did 3 passes with no problems.

From another list I got the idea that maybe there is an issue with the graphics driver and I disabled all the fancy eye candy in the Visual Effects tab of the Appearance settings from the Preferences menu.

So far so good. I'll post up again if this seems to do the trick (but right now I'm posting from a Mac iBook because I can't get the dang wireless to hook up to my home network!)

---

### Post by ewinslow on 2008-11-06
Well, turning off the eye candy certainly did the trick. My system is stable and no Dazed and Confused messages in the system logs.

Now the question is what bug is causing those messages when even the moderate eye candy is turned on?

I'll have to search Launchpad at some point to see if a bug has already been submitted.

---

