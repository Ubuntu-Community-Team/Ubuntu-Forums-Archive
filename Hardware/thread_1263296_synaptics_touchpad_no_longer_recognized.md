---
title: "synaptics touchpad no longer recognized"
date: 2009-09-10
forum: Hardware
---

### Post by goesthefear on 2009-09-10
Total newbie here, I just installed ubuntu last week and I was tweaking my mouse the other night but now I fear that I've done something horribly wrong.

Basically, the bottom right and top right corners of my touchpad were acting as a right click and middle click, respectively, so I installed gsynaptics and enabled SHMConfig so I could turn it off. While I was at it, I changed the maxdoubletaptime to make it easier for me to drag'n'drop. Everything worked fine.

Then, I turned my computer on today to find out that the vertical scrolling on my touchpad is no longer working. When I go to system > preferences > mouse, the touchpad tab no longer shows up. So I did xinput list and found that my mouse is now being read as "ps/2 generic mouse." Also, whenever I try to do anything with synclient (aside from synclient -1), it tells me, "Can't access shared memory. SHMConfig disabled?"

I'm sure there's a very simple solution here, but I've spent a couple hours scouring the net and I can't for the life of me figure it out. I attempted to find a solution at this [troubleshooing guide]("http://web.telia.com/%7Eu89404340/touchpad/trouble-shooting.txt") but I don't really understand any of it.

Can anybody tell me what I've done wrong and how I can fix it? Thanks!

---

### Post by thegreatsnafu on 2009-09-10
Check synaptic if the software is still installed. It has happened to me before, when I restart my computer, software just disappears.

---

### Post by goesthefear on 2009-09-10
yeah, I thought that might have been the case but it says it's still installed and that it's the newest version.

---

### Post by thegreatsnafu on 2009-09-10
Then try re-installing it...

---

### Post by goesthefear on 2009-09-10
unfortunately, re-installing doesn't seem to do anything. I fear I may have really messed something up.

---

### Post by thegreatsnafu on 2009-09-13
Try completely removing the software, and see if it works without it...

---

### Post by goesthefear on 2009-09-14
I removed gsynaptics but everything's still the same. :(
Thanks for all the suggestions, though!

---

### Post by thegreatsnafu on 2009-09-15
Yeah, sorry about all the trouble. Your transition to Ubuntu has not been as smooth as most. The only thing I can suggest is to wipe your drive and start over (Just as long as you haven't done to much stuff with it, e.g., documents, pictures, etc...). That's what I do when I screw things up beyond repair...

---

### Post by goesthefear on 2009-09-16
Eh, it's all right. It shouldn't be too bad to start over. I just installed ubuntu a few weeks ago and despite this trouble, it's worth it.

Thanks again!

---

