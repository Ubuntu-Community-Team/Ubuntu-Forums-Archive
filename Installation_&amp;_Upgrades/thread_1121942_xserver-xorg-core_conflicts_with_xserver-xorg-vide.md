---
title: "xserver-xorg-core conflicts with xserver-xorg-video-4"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by darkzerox on 2009-04-10
I was having some problems with some touch buttons on my laptop, and I was hoping 9.04 might fix them. Surely enough, it did, but broke everything else.

Anyway, xserver-xorg-core was not installed properly during the setup, so I'm trying to manually install it with apt-get, but it's telling me it conflicts with xserver-xorg-video-4, and nvidia-glx-180 provides xserver-xorg-video-4 and is present and installed.  But I can't remove that either because a ton of things depend on that....

So what can I do? How do I upgrade xserver-xorg-core?

---

### Post by darkzerox on 2009-04-10
Forget it. I fixed it. I am genius.

Said I couldn't reinstall xserver-xorg-core because it depended on something else, but I couldn't uninstall that because that depended on something else, and those too depended on something else (I think there were some circular dependencies in there?!)... anywho, I uninstalled the crap out of all of them in one command (and scribbled down what I was uninstalling on a notepad so I could reinstall em later)...then installed the new core, and now everything is happy. Go me!

Let's hope the nvidia drivers don't explode now...

---

