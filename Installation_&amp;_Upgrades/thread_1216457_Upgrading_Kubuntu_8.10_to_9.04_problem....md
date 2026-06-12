---
title: "Upgrading Kubuntu 8.10 to 9.04 problem..."
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by ShadeS_07 on 2009-07-18
I am a bit frustrated since I have just finished doing a distro upgrade of my Kubuntu 8.10 to 9.04, it was working and I was able to login graphically with 8.10 until this upgrade I just did...

Ok, here's what happens... After the loading screen of Kubuntu, (you know, that blue progress bar... :p), you would expect a nice graphical log in screen for you to type in your user name and passcode... but, in my case, it won't reach to that point... I would be ending up in this text mode log in screen, which I believe is a virtual terminal....

Upgrade was smooth, no errors, btw it might be useful for you also to know that I have decided to keep obsolete packages.. (I mean at the post installation, the "Cleaning Up" stage of distro upgrade.. where I was asked whether I want to "Keep" or "Remove" these packages...), dunno if that'd be something to cause this problem...

Perhaps, this has something to do with my graphics card? Hmmmmm, I have actually encountered this problem before when I was using Kubuntu 8.10... I was using an ATi 9200 gfx card when it got busted so I changed it to NVIDIA GeForce FX5200 (Albatron)... After the change of gfx card, I encountered the same problem I am having now... or maybe similar? -_+

What I did to resolve the problem was, I logged in with my account with vt... I did two things... Dunnno if they're right/necessary, but I just did and it worked that time... 

I did..
```
sudo apt-get install nvidia-glx-173
```

and,
```
sudo nvidia-xconfig
```

then
```
sudo reboot
```

...the next boot worked, ended me up with the graphical login screen... problem solved... :D


So a while ago, I did the same, but since it wasn't working anymore (I believe) with **nvidia-glx-173**, I then tried, **nvidia-glx-180**, but unfortunately, still with this problem... (grrrr...)



So now, I am using a different OS to ask help from you peepz to resolve this problem of mine....


You might find it useful to know what my specs are... :D :popcorn: -_+

AsRock Motherboard P4VT8+
Intel Pentium 4 HT 2.80 Ghz, 2.80 Ghz
1 GB RAM (3 Samsung M3's PC2100 DDR1 SDRAMs, 256 MB + 256 MB + 512 MB)
NVIDIA GeForce FX5200 (Albatron) 256 MB VMemory, DDR 128-bit

~Thanks in advance... God bless always... :D :popcorn: :guitar: :)

---

### Post by ShadeS_07 on 2009-07-18
*bump* :popcorn:

---

### Post by ShadeS_07 on 2009-07-19
Is it a serious problem? Can it be resolved? Seems that no one knows how to resolve this... :(

---

