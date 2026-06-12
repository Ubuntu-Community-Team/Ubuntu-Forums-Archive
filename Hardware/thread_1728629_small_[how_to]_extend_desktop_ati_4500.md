---
title: "small [how to] extend desktop ati 4500"
date: 2011-04-14
forum: Hardware
---

### Post by wmb on 2011-04-14
I saw some old threads online where people were having problems  extending their display. (For me) It was as simple as:

Turn on and hook up your external monitor.

System -> Preferences -> ATI Catalyst Control Center (Administrative)


On the left, under Pages I saw: [this (click)]("http://i.imgur.com/pY41W.png")
Welcome
Information
Color
+Display Manager
Display Options
+3D
PowerPlay
Preferences

[I clicked]("http://i.imgur.com/ETsw4.png") "Display Manager"

I then had something that looked like a laptop (with a 1) and a separate monitor (with a 2).

When I say (with a 1), it's labeling your monitors 1 & 2.

Below that I saw:
Display Properties and Multi-Display

[I clicked ]("http://i.imgur.com/zbxzP.png")the separate monitor (with a 2), and then Multi-Display. There was no reason to change any options for my current display that looked like a laptop (with a 1).

Under Multi-Display (separate monitor (with a 2)) I clicked: "Cloned display from display(s) 1".

[My four options were:]("http://i.imgur.com/RNbTI.png")
"Disabled display"
"Single display desktop (multi-desktop)"
"Cloned display from display(s) 1"
"Multi-display desktop with display(s) 1" <-------- I selected this.

And restarted my computer. Tada. Hopefully this will save people from installing 3rd party drivers. I just wanted an extended desktop to use so i didn't have to switch "windows" to compile when working on my projects. Good luck.

[http://i.imgur.com/pY41W.png](http://i.imgur.com/pY41W.png)
[http://i.imgur.com/ETsw4.png](http://i.imgur.com/ETsw4.png)
[http://i.imgur.com/zbxzP.png](http://i.imgur.com/zbxzP.png)
[http://i.imgur.com/RNbTI.png](http://i.imgur.com/RNbTI.png)

Dell Laptop Studio 1555 Linux Ubuntu 10.10 extend desktop external monitor ATI Radeon Mobility 4500

Good luck :)

I know this isn't hard for most people, I just saw that people were having trouble with it and figured I would post a quick tutorial.

---

### Post by Syndaryl on 2011-07-28
Thank you WMB, found your tutorial and it's quite helpful - but I have a question of course. Lo these many months later.

Catalyst makes me restart, and then when I boot up again... it's switched to "Cloned display from display(s)", where everything is duplicated on the two screens. Which would be useful for presentations or co-op games but not so much for getting more workspace :(

Any ideas? Or anyone else?

---

### Post by dínü on 2013-01-12
@wmb, awesome tutorial :)

currently, I am using 12.04 and **one extra step** is required to get the multiple display working. After you have restarted the computer, go to

system settings - > Displays

untick the mirror displays checkbox, click Apply and Viola! ;)

---

