---
title: "Touchpad Issues on Eee PC 900HA"
date: 2009-04-26
forum: Hardware
---

### Post by Ripp_Steakface on 2009-04-26
Hey guys, I'm completely new here. I got an Eee PC 900HA (160GB HD) a few weeks ago, and I'm now dual-booting both Windows XP (which it came with), and UNR 9.04. I'm also new to Linux so I'm still learning the commands and everything. I've had some network issues with it connecting to my Airport Extreme base station, but it seems to be going a bit more smoothly now.

Anyway, to the point. This small trackpad is giving me problems; the cursor is very jumpy. For example, say my cursor is in the upper right quarter of my screen and I'm not touching the trackpad. I put my finger down anywhere on the trackpad, and the cursor jumps 2 to 3 inches to the left. It seems to want to go to the left more than the right, but it may just be the way I'm testing it. It hasn't done it in a vertical motion yet. Could this be simply a poor quality touchpad, or could it be in the software? Any help is appreciated. If I need to enter Terminal commands, be sure to go easy on me, I'm still learning. Thanks!

Edit: I should mention that it doesn't do this in WinXP.

---

### Post by djwishbone on 2009-06-16
Bumping this because I have the exact same issue.  This does not occur in Easy Peasy, but I know that it was based on a previous version of Ubuntu.

---

### Post by buddyd16 on 2009-06-18
Bump as I also am experiencing this. 

One solution I found is to create/edit an options.conf file in the /etc/modprobe.d directory

```
 
cd /etc/modprobe.d
sudo gedit options.conf

```

and add the line 
```
options psmouse proto=imps
```

the only problem with this solutions is you lose the touchpad tab under mouse options and the ability to disable tapping.

anyone know of an alternate solution to smooth the mouse or an additional line for the options.conf file that will disable tapping?

---

### Post by 12ftguru on 2009-06-18
Oddly enough, when I check "Enable mouse clicks with trackpad" the jerky mouse problem goes away. If I uncheck it, the cursor frequently snaps back across the screen when I try to move it from one side to the other.

Not a huge fan of mouse clicks on the trackpad, but it seems to be the only way the trackpad is useful for me.

Anybody else able to confirm this?

---

### Post by djwishbone on 2009-06-19
I can't stand tap to click features, but it's interesting that you've at least discovered some work arounds.  I'll keep messing with it to see if I can make it work.

---

### Post by paxmark1 on 2009-06-25
hi, could tap the touchpad screen to left click in xandros (GATE, GATE, PARAGATE, PARASAMGATE) live peasy, installed eeeubntu base, but not in installed unr 9.04 or unr 9.10rc2 presently.  In gui the enable mouse clicks is enabled.  I can only clicck via the silver buttons.  have not investigated command line options or any .conf yet.  peace mark

---

### Post by Ripp_Steakface on 2009-07-17
Hey all, I remembered that I put this thread up a while back and checked it out. I'll take a look at the touchpad tapping options to see if enabling it fixes the issue. I'd probably rather enable it than deal with this jumpy cursor. I dislike the touchpad tapping that laptops support, but I hate the jumpy cursor more. I hope this issue gets cleared up in a new version or update.

Update: Still jumpy. At first it seemed to be somewhat better, but when I took my finger and touched the left side of pad, then the right, then the left, alternating like that while lifting my finger a good distance away from the pad, I had a few occurrences where the cursor jumped 5 or more inches to the right to the edge of the screen. Quite frustrating. If I didn't have this issue, the XP side of my HD would be quite lonely.

Is there a way to submit bug info?

---

### Post by hibliss on 2009-07-17
Do you have the array kernel and EEE Control package? 

I can disable my taps without a jumpy mouse on my Eee, but I am running Eeebuntu.

---

### Post by djwishbone on 2009-07-29
What version of eeebuntu are you running.  I'm currently running the latest, which I believe includes the array kernel and eee control package?  I still have the jumpy cursor issue.

> **hibliss said:**
> Do you have the array kernel and EEE Control package? 

I can disable my taps without a jumpy mouse on my Eee, but I am running Eeebuntu.

---

