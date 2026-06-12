---
title: "Keyboard not working properly (Euro-Symbol, (at)-Symbol, Arrow-Keys)"
date: 2008-11-27
forum: Hardware
---

### Post by DaVinciXL on 2008-11-27
Hey there.

I upgraded to Ubuntu 8.10 from 8.04 a few days ago. I spent the most time since then, trying to get my keyboard (standard keyboard, 105 keys - worked for the last 6 years or so).

I've always used a German layout (dead grave acute), however, the following problems occure with all layout (even us-english ones).

1. The Arrow Keys
Left, down, right don't work at all - up takes a screenshot

2. "Alt Gr"-Key
Doesn't work at all. Well, with some layouts it has the same functionality as the enter key. This is the most annoying thing because I cannot type the Euro- and the "at"-Symbol.

3. Division-Key on NumPad
Depending on the selected layout it produces nothing, a line break or duplicates the function of the Insert-Key - it never produces a slash.

Any ideas?

Thanks in advance!

---

### Post by eantoranz on 2008-11-29
I'm having exactly the same problem... BUT I noticed that the problem happens in "X". In the VTs the keyboard works like a charm.

I'm using kubuntu intrepid with the nvidia driver on a Compaq V3317la box.

---

### Post by eantoranz on 2008-11-29
I just noticed another thing. On KDM, the keys work normally too. So the problem is only happening on KDE.

---

### Post by eantoranz on 2008-11-29
Well.... you never know where you're gonna get when debugging.

Look... I shutdown kdm (sudo /etc/init.d/kdm stop) and started kde "by hand" by the terminal:

```

X &
DISPLAY=localhost:0.0 startkde

```

and then guess what happened? Fist: I got the keyboard to work properly (arrows and altgr too @@@@@@). Second: There's a message that I was getting when starting my kde session about one application crashing.... well, I didn't see it when I started kde by hand. Third: when starting kde by kdm, I didn't get direct rendering, but by hand I do get it (and compiz can be started).

So.... I have a hunch that the problem is in KDM. Any idea of how to solve this?

I'll post a bug on launchpad and let's see what they say.

---

### Post by eantoranz on 2008-11-29
Let's see what they tell me:

[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/303576](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/303576)

---

### Post by _Smiler_ on 2008-11-30
> **eantoranz said:**
> Let's see what they tell me:

[https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/303576](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/303576)

I do what it says here (which is what you've already posted?) and it says command not found. I have a very similar problem, I have a german computer and thus German keyboard with Ubuntu installed. I have the "German" layout selected, default variation. Ctrl (on this keyboard it is Strg) + Alt doesn't to produce for example the at symbol or euro symbol, BUT if I press Shift + Alt Gr (Right Alt? I've never understood the difference...) + Q, I get &#937;. These aren't marked on the keys, and if I use Shift+Alt Gr with virtually any key I get strange and interesting symbols which aren't marked on the keys. So, obviously a layout problem but I've tried them all......

---

### Post by eantoranz on 2008-11-30
Maybe you're using ubuntu instead of kubuntu. Which command is not found?

In the VT, you have to do this sequence:

```

sudo /etc/init.d/kdm stop
X &
DISPLAYstartkde

```

But that's because I'm on kubuntu... on ubuntu, it should be gdm instead of kdm and start-gnome or startx or something like that (I honestly have NO idea of how to start gnome from the terminal). However, if you are using gnome, then I don't think the problem I descrived applied to you, cause I think the problem is somehow related to KDM, not GDM. Anyway.... we'll see.

---

### Post by DaVinciXL on 2008-12-02
Well... I'm running Ubuntu with GDM...

---

### Post by merlin666 on 2008-12-03
Same problem here with Gnome and a US keyboard laptop. The arrow keys do not work, I noticed it first in terminal when I wanted to recall a few commands after upgrade to intrepid :(

---

### Post by TimsterC on 2008-12-03
I'm having a similar problem.

System: ThinkPad W500
Ubuntu: 8.10

Problem: arrow keys work fine.
         DEL stops music playing (If I turn off the numlock the keypad works ok so the DEL key there works)

Very strange issue. Tried the ThinkPad keyboard layout and Generic.

Same thing happens on my MS Natural Ergonomic 4000 but that's an entirely different beast.

It all worked fine in 8.04 LTS :)

---

### Post by DaVinciXL on 2008-12-17
Push.

---

