---
title: "Laptop and External Monitor"
date: 2011-05-30
forum: Hardware
---

### Post by LinuxLearner123 on 2011-05-30
OK, so I have an HP Pavilion laptop, which is happily running Ubuntu 11.04. I just received a Dell Trinitron display (no, I haven't heard of that one, either) and connected it to the laptop via VGA. It mirrors the image fine, but when I try to have it acting as a separate display, I get an error message saying:
"The selected configuration for displays could not be applied
requested position/size for CRTC 148 is outside the allowed limit: position=(1280, 0), size=(1280, 800), maximum=(1600, 1600)"
Like I said, it mirrors just fine.
I'll attach a screenshot of the notification to this thread.

---

### Post by livit on 2011-06-01
Oh, why did I upgrade to Natty Narwhal? From now and on I will follow the motto "If it works, why upgrade if you don't know it holds a new feature that you want."

Before Natty Narwhal I ran two screens at the resolution 2390x1532. Now times has got rough, and I am currently searching all over the internet for a solution. I will report here if I find anything. 

xrandr could be interesting, or xorg.conf, but I am a newbie and don't really know. Yet.

---

### Post by livit on 2011-06-01
I'm sorry, because I cannot solve your problem. However, I managed in some way to get it to work with my screen, so I can give you a hint. It is rather late now, so I wont try to recreate the issue right now, but I will try tomorrow.

I changed some settings in xorg.conf, and that ended up in a black screen on restart. Apparently it's quite dangerous to change xorg.conf without knowing how to change it. I restarted in recovery mode and replaced my modified xorg.conf with an older version. Then I restarted and it worked flawlessly. Ok, not compared to 10.10, but still, it works.

I would guess that the restart solved my problem. I hadn't actually restarted after connecting the screen, so maybe the virtual desktop resizes itself if a secondary screen is connected at startup.

---

### Post by livit on 2011-06-04
I did not manage to solve the problem that occurs when you connect a second screen when the system is up and running. The solution for me was simply to restart the computer with the second screen connected.

So I guess the main problem is still remaining to solve...

---

### Post by LinuxLearner123 on 2011-06-06
OK, I have 'fixed' the problem, or at least found a work-around;
the display can be used separately by simply moving the little placement picture to show that it is either _above_ or _below_ the main monitor (above would make the new monitor the main one), instead of to the left or right. This may take some getting used to, but it worked in both GNOME (and Ubuntu's spin with the launcher) and KDE. The results are the same (the launcher in Ubuntu's version of GNOME is only on ONE of the desktops, not all the way down the side of both), but to get from one desktop to another, you move the mouse to the top/bottom of the screen, rather than to the side. This is not the best work-around, but it's good enough that I will mark this thread as [solved].

---

