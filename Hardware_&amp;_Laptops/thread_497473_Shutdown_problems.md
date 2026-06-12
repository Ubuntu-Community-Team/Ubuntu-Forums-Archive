---
title: "Shutdown problems"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by randal on 2007-07-10
I've got Feisty on my laptop. I'm having several problems when I shutdown.

First, my screen gets messed up with blocks of colors like those in TV networks when they're off air. Sometimes, the screen is just all messed up with colored noises like those in TV networks when the signal is interrupted. In the second case, the shutdown would not complete--the system just stays like that. Sometimes, especially when I close the laptop lid after telling the system to shutdown, the screen is just turns black but the computer is still on and nothing's going to happen; it just freezes.

This happens in varied times and I'm not really sure what causes this. I'm getting worried that taking the battery off every time--it's becoming more frequent recently--is going to fry my hardware.

Addition: I've also experienced having the system in halt while using it while the mouse/cursor remained working--and it can't click on anything.

---

### Post by randal on 2007-07-12
Still no replies?

---

### Post by tekkenlord on 2007-07-16
Hi, I am experiencing a similar behaviour (I use Kubuntu 7.04). I have thoroughly searched the internet for this problem an was able to find a workaround (works for many but not for me). Anyway, what you have to do is edit the /etc/kde3/kdm/kdmrc file and add or uncomment the following line to the [X-:*-Core] (note the *) section:

TerminateServer=true

Hope it helps! If this does not work I may have some other suggestions to make.

---

### Post by randal on 2007-07-17
Thanks.

I tried this one but I'm not sure if it really works... you see, my problems on shutting down the system occurs at random times. I'll just report if I get problems again.

---

