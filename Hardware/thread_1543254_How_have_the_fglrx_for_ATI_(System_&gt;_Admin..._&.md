---
title: "How have the fglrx for ATI (System &gt; Admin... &gt; Hardware...) going?"
date: 2010-07-31
forum: Hardware
---

### Post by RJ12 on 2010-07-31
Well upon installing Ubuntu 10.04, I was asked if I wanted to enable the restricted drivers for my ATI card. I did some research on the fglrx driver and everyone seems to be saying they are not really working the way it should be. I can't remember what specific graphics card I have, but I know its a Radeon, if someone can give me a terminal command to find this out, I would be happy to post it. But these posts that I have found are a little old. I just want to know if the drivers have matured yet or if they are still really bad. My card could probably use the drivers because anything full-screen seems slow, and with the 3d effects, they get choppy. I tried running GNOME-Shell and had a few problems, like it being really sluggish and some icons being weird and random colors. Also the Plymouth splash screen never really gives me progress of whats happening. I mainly get a black screen with a underscore for a few seconds, then the splash appears real quick and disappears to the login screen (I don't even get to see the dots moving:() I just want to have better performance, because when I used the drivers in Karmic, it did improve. Sorry for the long post!

---

### Post by freenity on 2010-07-31
Try
lspci | grep VGA

I have ati adeon 3450 and the proprietary drivers that come with lucid didn't work very well for me while using compiz, it was a little slow, I downloaded latest drivers from the ati website and installed them using this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Now it works great.:)

---

### Post by RJ12 on 2010-07-31
I have this graphics card

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
```

---

### Post by RJ12 on 2010-07-31
I'm starting to think this is in the wrong section. I will repost it in General Help.

To Admins: You may close / delete this thread. You may also move my new one in General Help to where it best belongs.:p

---

