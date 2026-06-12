---
title: "Dead screen"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by Chepe on 2008-03-15
I've got a pretty new Dell xps m1330 laptop on which I'm running Ubuntu. Everything has worked perfectly until now. A couple of hours ago I set my computer in suspend. When I got back and tried to wake it up, the screen was dead. That happens quite often, so I thought it could be fixed with a reboot. But nothing happened when I tried to reboot, not even the dell logo that is the first ting I usually see appeared. It seems like the screen is completely dead. 

I think the video card is working, I am currently using the laptop using an external crt-monitor. Is it possible that the suspend has done something to the computer's settings? It seems like the screen gets power, or at least there is a little blue light right next to the web-cam which is sometimes turned on. 

Do you think it is a hardware problem or is it possible that there are some settings I can change?

All help is appreciated!

Update:
I just ran a Diagnostic test (under Bios) and the the screen started and lots of clolors appear, so the screen seems to be working, it just isn't turned on when the computer starts...

Update 2:
I ran the diagnostic test again, and now I got two error messages: (I probably got the same messages the last time as well, but I didn't see them since the external screen wasn't conected..)
error code 0321
msg: Error code 2000-0321
msg: unable to detect LCD


error code 0326
mag error code 2000-0326
msg:lcd inverter error, unable to turn lamp ON. Vendor. -revision :0

Does this mean that I have to go to some sort of support shop?

---

### Post by Glaxed on 2008-03-15
It sounds like Ubuntu has been a catalyst, but not completely responsible for frying your screen. Is there a tech shop you can take it to?

---

### Post by Chepe on 2008-03-15
That's exactly my problem, I'm currently not at home (I'm up in the mountains). I can take it to a shop when I get home, but I could really need my computer the next week.

However I just ran a Diagnostic test (under Bios) and the the screen started and lots of clolors appear, so the screen seems to be working, it just isn't turned on when the computer starts...

---

### Post by Glaxed on 2008-03-15
Right, so perhaps a connection inside your laptop to the LCD screen is broken or disturbed.
Any proof of this?
> 
msg: unable to detect LCD

but obviously, you *do* have an LCD.
The diagnostics you ran were visible via the CRT screen, right? (Not on your laptop).
If so, it's not Ubuntu's fault, it may be that you just bumped your laptop in an unfortunate location. This is just a random theory.

Good luck!

ps; if this doesnt get fixed soon, consider taking it to a shop later.

---

### Post by Chepe on 2008-03-16
Yeah, I might just have bumbed it... I've got no proof of any cables not being connected, but I'll see if I can get some tools and open it up a bit.

The strange thing is that the first time I ran the diagnostic test I didn't see any text on my laptop's lcd screen, but it showed lots of colors, or more precisely lines of varying color. When I ran the diagnostic the second time I connected the crt-monitor, and that was when I saw the error message. So it seems like it is possible for the screen to be turned on..

It seems most likely that it's not Ubuntu's fault, so I guess I'll just call Dell support when I get home and get them to send a technician to my house..

Thanks for the help!

---

