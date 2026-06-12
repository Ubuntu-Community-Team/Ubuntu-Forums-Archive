---
title: "Keyboard/typing lag in Dapper"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by FarmerDave on 2007-03-15
I just switched my home linux box from FC4 to Dapper (6.06.1).  Everything seems to be fine, except that there's a really long lag while typing.

When I type a key, it can take up to .5 sec or more for the character to show up.  If I type any faster than about 2 keys per second, keypresses start getting dropped.

My USB mouse, however, is working great.

I've got a stock Dell Optiplex GS240 (boring desktop tower computer) that ran FC4 fine for years.

I get the same problem with both of my USB keyboards: an MS Natural Keyboard Elite, and a Belkin "Classic Keyboard".

It doesn't happen, though, when I plug the Natural Keyboard into the PS2 port, so it's got to be a USB-level problem. (Wow, I  wish I had tried that earlier-- this sentence took way less time to type.)

I looked into the "remove plptools" thing that other threads talked about, but it doesn't help; I don't even have plptools installed.

There are no complaints on dmesg or syslog, but I wouldn't really expect there to be.

I'd love to find a fix for this in Dapper; I've got to use it (can't upgrade to Edgy etc.) because of work.

---

### Post by Pilot-Doofy on 2007-04-03
I'm having the exact same problem. My typing is actually locking up as I type this out. :( But I think I found the root of the problem. It seems my browser has type lag mainly when a textfield has a background.

For instance, when I post on newgrounds.com, their forums posting page has a textarea with an image for a background. It seems to be MUCH worse on that page than this one.

---

### Post by lost_sole on 2007-04-20
I had a similar problem to this in Fiesty and found that it was an irq conflict. Adding irqpoll to the boot options solved my issue..

[http://ubuntuforums.org/showthread.php?t=412553](http://ubuntuforums.org/showthread.php?t=412553)

---

