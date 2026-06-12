---
title: "Two little problems on Vaio with feisty."
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by CheeseEatingBulldog on 2007-05-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/74672](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/74672) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				My gf had a Sony Vaio lying around and claimed it was 'broken', she was right to the point that windows on it was broken. Anyway I installed Feisty on it and it runs like a dream except for two things:

I myself have a Vaio and had a wifi pcmcia card with it, which works fine under Edgy, it slotted right into my gf's vaio, no prob, but I couldn't get it to log on to my network, so after some digging I found this:[launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/74672") which is exactly what is happening, namely that the last character of the essid is being lost, and by sudo iwconfig wlan0 essid linksysZ (the Z being added character that is lost) it can be fixed. But this means doing that each time I log in. Any ideas as I want to upgrade my own vaio to feisty soon too, and don't want to run into this again.

The second problem is a problem with the gl-desktop, it works (her vaio has a 16mb ATI card) but when I fullscreen any window I loose the mini-maxi-close buttons on the top. They are still there (as when I hover above where they should be I see the yellow hover-over tags), but all white. This happens with all themes except the default one (if I unclick the use metacity theme there are visible at fullscreen).

Thanks in advance.

---

### Post by CheeseEatingBulldog on 2007-05-21
Doesn't anybody have an idea or two?

---

