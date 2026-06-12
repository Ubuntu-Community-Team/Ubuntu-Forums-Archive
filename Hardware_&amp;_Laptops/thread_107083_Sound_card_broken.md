---
title: "Sound card broken?"
date: 2005-12-22
forum: Hardware &amp; Laptops
---

### Post by phoenixy on 2005-12-22
Hi,

I have a gateway mx7515 laptop with a built-in conexant sound card. My machine dual boots ubuntu and winxp. Everything work fine until awhile ago. 

What happened was that I was playing a game of Homeworld2. Then all of a sudden, the game crashed. This is not the first time it crashed on me, so I didn't think much of it. There was still music from the game, and I can move the mouse around. Other than that, there is not much I could do. So I turned off the computer and rebooted it.

Now here comes the interesting part. After rebooting the computer, the sound device is gone. First thought that comes to mind is Windows screwed up again and fudged the sound card driver. Before I do anything, I boot into ubuntu and see if it is really a Windows issue.

To my  surprise, Ubuntu also reports no sound card. /dev/sound is gone. None of the app can detect a sound device. Sure enough, lspci/lshw shows nothing.

Anybody experienced this before? Is it time to send my laptop in for repair?

---

### Post by fordfan753 on 2005-12-22
Ouch, this doesn't sound healthy. I'm not hardware expert, especially laptop hardware, but if both operating systems can't see the sound card, well, it rules out software issues. I think it may be a good idea to take it in somewhere to get someone to look at it. And don't let them give you any crap about using anything that isn't Windows.

---

### Post by phoenixy on 2005-12-22
HMMM...

what do I know. I shut off the machine for 3 hours and now the sound is back.

Overheat issue? My laptop is rated AMD4000...

very strange

---

