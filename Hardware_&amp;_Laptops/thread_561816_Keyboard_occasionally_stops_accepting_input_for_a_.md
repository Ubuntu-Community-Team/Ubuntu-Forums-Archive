---
title: "Keyboard occasionally stops accepting input for a few seconds"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by marquarc on 2007-09-28
This error is a bit difficult for me to describe. It's by no means a deal-breaker for me, regarding Ubuntu, but it is a bit annoying! 

I have a USB Microsoft Natural Ergonomic Keyboard 4000. Every minute or so, for about a second, the keyboard will stop accepting input. It works just great, otherwise. But for that second it will ignore anything coming through the keyboard, and just leave the cursor where it is. It will not buffer and catch up, so it will leave me in the middle of a word, and I'll have to go back and retype things. For example, I'll be typing the phrase "dangerously repugnant" and it'll come out on my screen as "dangugnant". During these times, all other processes act completely normal. XMMS keeps playing music, I don't notice any blips in my video games (Starcraft on Wine, woo), and the USB mouse input is completely fine. 

This happens often enough that it gets really annoying, but I have no idea where to start troubleshooting the issue. I don't want to just give up and get a new keyboard, because I really like this one. So far, all I have done to try to fix it is to change the Keyboard model in System > Preferences > Keyboard. I tried a few different ones, but it didn't make a difference. 

Anybody have any ideas on how to troubleshoot this one? 

Corey

---

### Post by dabl on 2007-09-28
I would, in a console window, enter ```
top
``` and then put that window somewhere where I could see it while typing.  "Top" shows your running processes listed in descending order of resource consumption, and one of the columns shows the percent of CPU utilization. At the point where your keyboard "freezes", I'm guessing that top will show some other process(es) running your CPU up to 100% for a few seconds.  Then you'll have to decide what to do about it, based on your priorities ....

:)

---

### Post by peabody on 2007-09-28
Is this the only computer that this happens to with this particular keyboard?  Have you tried typing on it for extended periods of time on other computers to see if maybe it's a hardware problem with the keyboard?

You could try booting into a Knoppix LiveCD and typing with it for a while to see if you have any problems that are similar.

---

