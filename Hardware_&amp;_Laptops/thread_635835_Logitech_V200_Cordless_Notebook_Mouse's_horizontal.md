---
title: "Logitech V200 Cordless Notebook Mouse's horizontal motion inverted"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by Aeren on 2007-12-09
I just bought a new USB logitech mouse for my Vaio laptop (VGN-FZ18E) with Ubuntu 7.10 installed on it, and it's been acting quite weirdly. My horizontal motion (not even the horizontal scroll) is simply inverted! The vertical motion works just fine though.
I've been searching a bit through the forums, but haven't seen anything refering to that kind of problems. Does anyone have an idea as to what I can do?

---

### Post by Aeren on 2007-12-09
Apparently I was wrong. It is not the horizontal motion that's been inverted, it's simply the motion axis that has tilted by 45° to the left. Please, help me! I couldn't find any option that would let me change that.

---

### Post by soaringphx on 2007-12-12
Sorry if this is dumb, but make sure that you are not working on a grained surface.  I notice this issue when I work on my grained wooden table at an angle (it sees the lines and gets confused about its direction).  When I reorient myself so I am parallel or perpendicular to the grain, the mouse works great.

---

### Post by xecure on 2008-02-07
i have the exact same problem when i am viewing a pdf file with Evince Document Viewer 2.20.1. When i try to use the left and right tilt under firefox nothing happens at all. Any have a solution to this problem?

---

### Post by xecure on 2008-02-09
ok i dug through the forum and found a solution. First open up xorg.conf file by ```
sudo gedit /etc/X11/xorg.conf
``` and then go to the section where the identifier is "configured mouse" and add this line: ```
Option "HWHEELRelativeAxisButtons" "7 6"
```

that did the trick for me.

---

### Post by adi116 on 2008-02-22
my mouse - same logitech v200 wireless - wont scroll horizontally at ALL. i tried modifying xorg.conf file as stated aboe already, but nothing happened. i restarted my computer and everything - is there some sort of library or something i need to download? or is there any other solution to the issue?

---

### Post by adi116 on 2008-02-22
sorry for having the grammar skills of a two year old - i was up all night trying to finish typing a paper. livin off monster and repositories right now!

---

### Post by xecure on 2008-03-01
what does your configured mouse section say in your Xorg config file?

---

### Post by strider2k on 2008-06-07
Can someone post their /etc/X11/xorg.conf and/or /etc/udev/rules.d settings?

---

