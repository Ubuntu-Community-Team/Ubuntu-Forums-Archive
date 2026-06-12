---
title: "Glitch on window fade-in leaks an image I watched hours ago"
date: 2017-10-20
forum: Hardware
---

### Post by nachokb2 on 2017-10-20
Hey there,
  strange behavior here. Please bear with me.


[LIST]
[*]using Ubuntu 17.10; installed it in beta, upgraded upto Oct 18, there are probably lots of updates now given its official release;
[*]on an Ivy Bridge 3610QM (Intel HD 4000) laptop with Nvidia 650M using Optimus;
[LIST]
[*]discrete GPU is enabled because the HDMI output is connected to it;
[*]I'm fairly certain all rendering is done on the discrete GPU (`glxinfo` says it's Nvidia and I don't believe we'll have more flexible ways to render these things until EGLStreams, render nodes, or whatever ends up working);
[*]I'm using Xorg and Nvidia's proprietary driver (version 384.90)
[/LIST]

[*]I use Guake as my terminal of choice;
[LIST]
[*]it's a Quake-like console;
[*]the important thing for this bug: when you toggle it with a hotkey, it shows up in front of everything, with an animation (it fades in while applying a slight vertical translation);
[/LIST]

[*]the weird behavior I observe is:
[LIST]
[*]when fading in, I can see a flash of what's basically old content of video RAM;
[LIST]
[*]sometimes it's a webpage, sometimes it's an image;
[/LIST]

[*]this image is different evey time the animation is toggled;
[*]yet every 10 times or so, they repeat;
[*]about half the time it's garbage (say, mostly black with an images stretched or deformed by wrapping lines using a wrong value for width &#8213; please check attached video);
[/LIST]

[*]I also suspect that this leak is the cause for GPU crashes I see every few days;
[/LIST]

P.S. I managed to capture it in a video: [https://youtu.be/bWhmTYMp7qI](https://youtu.be/bWhmTYMp7qI)

– nachokb

---

