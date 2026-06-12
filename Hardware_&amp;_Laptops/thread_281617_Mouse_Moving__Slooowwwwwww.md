---
title: "Mouse Moving  Slooowwwwwww"
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by theaverageidiot on 2006-10-21
I've always had this problem with Ubuntu on my laptop: I've got one of those touchpad mouse thingies. I don't know how to describe it. You move the mouse by moving around your finger on the pad? Well, when I use that, my mouse moves so slow! It takes three swipes to go from one side of the screen to the other! I tried maxing out acceleration and speed in the Mouse settings but it doesn't even change it a little bit. When I plug in a USB mouse (which I don't always use because I use my laptop on my lap a lot :p), it goes at a fine speed.

Any ideas?

---

### Post by theaverageidiot on 2006-10-21
bump

---

### Post by theaverageidiot on 2006-10-22
Bumpety! Someone here's got to know something about my problem ](*,)!

---

### Post by DarkN00b on 2006-10-22
Click System->Preferences->Mouse to set acceleration and sensitivity in the Motion tab. These determine how fast your mouse moves.

---

### Post by theaverageidiot on 2006-10-23
I already did that, that's what I said in my first post. It didn't change anything.

---

### Post by Kishandr on 2006-10-25
Same problem with me too Did u fix it please reply

---

### Post by shiloh on 2006-12-15
my mouse is also extreamly slow - yes i maxed out under mouse settings - but its still amazing slow . i just tested 8 swipes across touch pad to get from one side to the other. PLEASE help - this is enough to force me off of umbuntu. (other boots do not have same issue)

---

### Post by ZERO_SHIFT on 2006-12-15
You can always use an external mouse if you want.

---

### Post by yngvi on 2007-02-09
hi,

also have the same problem on my dell latitude d820 laptop.
couldn't resolve the slow-mouse problem but just realized that there is some kind of joystick-like mouse in the middle of my keyboard. this thing reacts to changing mouse speed settings. so just using this now...would be interesting to get the touchpad mouse faster though.

---

### Post by rossgemuend on 2007-04-22
I am experiencing the exact same problem. I also have a D820 and I am using Feisty. Has anyone fixed this problem?

---

### Post by deadowl on 2007-08-19
ditto. I think it's a driver problem, still looking for a solution.

---

### Post by cschulte22 on 2008-01-21
I found a solution to this for my laptop (Latitude D820) over here: [http://www.ailis.de/~k/archives/14-Linux-on-Dell-Latitude-D820.html]("http://www.ailis.de/~k/archives/14-Linux-on-Dell-Latitude-D820.html")

Look in your /etc/X11/xorg.conf file for the InputSection for your touchpad device.  Add the following 3 options:

[INDENT][FONT="Courier New"]
Option         "MinSpeed"    "0.7"
Option         "MaxSpeed"    "3"
Option         "AccelFactor" "0.025"
[/FONT]
[/INDENT]

Restart X (ctrl-alt-backspace) and the touchpad should be moving a whole lot faster.

---

