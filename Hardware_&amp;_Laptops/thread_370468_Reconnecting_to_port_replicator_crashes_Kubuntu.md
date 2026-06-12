---
title: "Reconnecting to port replicator crashes Kubuntu"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by jmacdonagh on 2007-02-25
I have a Dell Inspiron 8600 and its standard port replicator. The first time I dock the computer (before it boots, or even after its booted), it works great. I can even undock the laptop when its on and it works great. The problem occurs when I *re-dock* it while it's still on. As soon as I re-dock, the system completely crashes. I can't restart X, I can't even get to a terminal.

When docked, the actual docking station has its power and "undock" button lit green. When I hit the eject button, the power light turns orange, and the undock button stops being lit. When I try and redock it, all the lights turn off, and my laptop freezes (cursor literally frozen).

Now, this must be a problem with my software, because my roommate has the exact same laptop, and the exact same docking station, and Kubuntu (same as me), and his works great. When he re-docks, both lights turn green like they should. I tried using his docking station, and it did not work. He tried mine, and it worked great.

I'm guessing this will be an extremely difficult problem to debug. Is there any way to get at the log files (which ones should I look at) to get a more descriptive error?

---

### Post by jmacdonagh on 2007-02-25
Just an update. /var/log/messages shows nothing that would help. It shows the messages saying all my connected USB devices are disconnected, but no messages when I plug it back in.

---

