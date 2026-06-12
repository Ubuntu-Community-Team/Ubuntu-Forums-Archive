---
title: "USB to HDMI Adaptor - Won't install"
date: 2013-05-14
forum: Hardware
---

### Post by VeryFoggy on 2013-05-14
I am attempting to connect my laptop running Ubuntu 11.10, to a Samsung DH02 (big fancy tv). As fancy as it is, there is no dvd player. I am attempting to hook the comp to the tv, so I can use the computer as a dvd player, etc. 

The guy at radioshack sold me two cords and said they should solve my problem. Problem is, I still have the problem.

I now have an Auvio USB to HDMI adapter and a 4 ft HDMI cable (it was not included with the adaptor).

I ran the install cd with wine and it failed to install. I ran it a second time, and it failed a second time. I have had issues with wine before so I went looking for a download instead. I have found nothing. 

I went ahead and plugged the cable in, hoping the computer might decide to be helpful and find a solution for me, but nope. 

Computer does not acknowledge that anything new has been plugged in. When I attempt to change the source on the tv to the HDMI connection that I plugged the cable into, the tv says "The source is not connected. Please check connection again."

Your thoughts?

---

### Post by VeryFoggy on 2013-05-14
[ATTACH=CONFIG]242599[/ATTACH][ATTACH=CONFIG]242600[/ATTACH]

Tried turing the computer off and tuning it back on with the cable attached. That was not a good idea, it didn't come up. So I unplugged the cord, cycled power again, and it ran through the safety checks, and then it came up. I tried running the setup file with wine, again. I have posted the screenshoots of the failed wine install.

---

### Post by VeryFoggy on 2013-05-15
Continuing on.

Found the website for the manufacturer which in theory is supposed to contain the drivers. [http://www.displaylink.com/support/downloads](http://www.displaylink.com/support/downloads)

They also have a link to a forum for self-help, [http://displaylink.org/forum/forumdisplay.php?f=29](http://displaylink.org/forum/forumdisplay.php?f=29)

which linked to another discussion, which I am too tired to understand. [http://askubuntu.com/questions/40031/how-do-i-use-a-displaylink-monitor](http://askubuntu.com/questions/40031/how-do-i-use-a-displaylink-monitor)

Anyway. I downloaded the first driver on the list. and opened it with wine. Got the same wine errors as before. 

Maybe it is just me. At this point I am planning to get a different adapter. ](*,)

---

### Post by davidbaumann on 2013-05-15
Please connect the adaptor and post the result of "lsusb".
Also I have the experience, some Devices only activate the HDMI input (so they can get recognized by the "sender") when the specified HDMI port is also selected as source.

You don't have to install the windows driver on Linux.

David.

---

