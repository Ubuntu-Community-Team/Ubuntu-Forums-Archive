---
title: "OpenGL on New Computer"
date: 2011-12-10
forum: Hardware
---

### Post by Kodeine on 2011-12-10
Salutations!

So I just got my new Lenovo H330 desktop computer. I've installed chrome and tried to play a game via NaCl entitled 'Bastion' but to my horror it says the game requires an OpenGL compatible graphics card. I know the new computer has an i5 CPU which has built in graphics but it doesn't seem to support OpenGL?

So does this mean I'll have to reuse the old nVidia geforce 6200 LE until I can get a new one? Further more if this is the case that the CPU's onboard graphics doesn't support OpenGL and I have to use my old one does this mean the inbuilt graphics are going to waste or will it still be used.

Thanks bye!

---

### Post by Kodeine on 2011-12-10
I've enabled NaCl but still nothing. Pocket legends loads half way and then says 'Oops! Your graphics have failed to initialize! You probably need to update your video card driver!' while Bastion still says about the openGL graphics card. If you saw what I said before disregard it as I haven't actually fixed it it seems.

Someone in ubuntu's help IRC channel has been helping me. We've tried installing ironhide and bumblebee and restarting xorg each time. When we used bumblebee one of the games that never worked did come on. I closed chrome, congratulated whom I was speaking to and went back to chrome only to find it didn't work again. Neither did any other games work. Why did it suddenly **** into working then suddenly die again?

---

### Post by Barbariandude on 2011-12-10
What we've tried so far:   - Adding a generic default xorg.conf  - Bumblebee  - Updating graphics drivers with ubuntu-x-swat.   None of these have worked, although he apparently gets intermittent moments where it works. I'm out of ideas.

---

### Post by Kodeine on 2011-12-11
Okay so from what I currently know. I have no graphics card. Only the onboard Intel graphics built in the i5 CPU. So according to others we don't need to mess about with bumblebee or ironhide. So the remaining question is why am I unable to run these chrome applications? Note that today 'Bastion' is giving me a different error.

Here's a montage of the errors. [http://www.fayp.com/vi-zCBtW8.png](http://www.fayp.com/vi-zCBtW8.png)

---

### Post by MoreOrLess on 2011-12-11
Post /var/log/Xorg.0.log

---

### Post by Kodeine on 2011-12-12
> **MoreOrLess said:**
> Post /var/log/Xorg.0.log

Here's the contents of that file [http://pastebin.com/9QWNpcX7](http://pastebin.com/9QWNpcX7) I'm now getting a third different error from 'Bastion'
```
Oh No! Bastion Has Stopped Working

This game requires a WebGL-compatible graphics card and that WebGL is enabled.

Please check to make sure you have a compatible card
with the latest drivers from your card manufacturer.
For a list of Chrome WebGL compatible cards, check out Chrome support.

Some versions of Chrome can disable WebGL,
please check chrome://flags to ensure it is enabled.

If the issue persists, please contact Supergiant Games.
```

---

