---
title: "My laptop is VERY noisy with ubuntu"
date: 2009-12-17
forum: Hardware
---

### Post by rpz79 on 2009-12-17
Hi fellas,

I've just installed 9.10 in my HP DV6282ea and when the OS is up the computer is very very noisy since it's a laptop I can't disassemble it and check exactly what is the source of the noise but I think one source of it comes from the CPU fan (which sometimes quietens) and the other one is just a constant "peeeeeee" as wild guess that it comes from the screen.
Both of them doesn't seem to come from the sound device (because I mute it ans still the "peeeee" remains) and neither of them exists on this scale longitude in MS Windows XP Pro SP3 (my other installed OS).

I hope you can help me solve this riddle...
THNX M8's
:guitar:

---

### Post by Marlonsm on 2009-12-17
Is the air comming out of it hotter than in Windows? And how is the battery life?
Most of the times, problems like this happen because Ubuntu isn't scailing well to the computer, requiring more processing power and producing more heat. This extra heat causes the fan to run faster, increasing the noise and reducing the batery life.

---

### Post by jaansson on 2009-12-17
I have kind of the same problem. Well, not the "peeee" problem, just the fan. Before it used to be so nice, since my laptop was very cool and quiet in ubuntu, but very loud with vista. But lately it has become loud most of the time, and the air coming out is so much hotter. And the whole underside of the laptop gets so hot, I can barely have it in my lap. 

It is really annoying, and I would get really happy if there was a way to make it quiet again.

EDIT: Just found out that my temp atm, with just firefox open is 65C

---

### Post by rpz79 on 2009-12-17
It cannot support the computer without direct AC connection.
I've set my CPU to on demand and he's most of the time at 1 of 1.83Ghz possible.
Still that noise exists it's a constant "peeeeeeee" and it's not a vent.
Where can I see the CPU and other peripherals heat ? 
Something I did notice that when software is installed or uninstalled suddenly the noise ends and when the action is finishes it returns, I don't know how to explain it...
A BEAST OF DIFFERENT KIND
:confused:

---

### Post by Marlonsm on 2009-12-17
Maybe it's the system beep... the one that should have been removed from all computers some 10 years ago. I'm not in Ubuntu right now, but I think that in the system preferences (maybe in "sound") you have the option to disable it.

---

### Post by jaansson on 2009-12-17
> **rpz79 said:**
> 
Where can I see the CPU and other peripherals heat ? 


I just activated a screenlet that showed the heat :P

---

### Post by rpz79 on 2009-12-18
To generelize what I've previously said is **whenever the HDD is active the "peeeeeeeeee" sound dissapears** and that noise is just too annoying for me so I've returned to Windows.

Yes I'm now also using screenlets and the Netmonitor doesn't show the network traffic I've tried with all the connections.

---

### Post by rpz79 on 2009-12-18
When the sound preferences is open in background the "peeeeeeee" disappears.
Can you take it from here guys ??

:rolleyes:

---

### Post by Marlonsm on 2009-12-20
Weird... just opening it shouldn't have any effect.

Try the following guide: ( [http://guvnr.com/pc/ubuntu-kill-system-beep/](http://guvnr.com/pc/ubuntu-kill-system-beep/) )

-Go to System > Preferences > Sound
-Uncheck "Play alert sounds"
(you'll need to reboot to see if there are any changes)

If it doesn't work, go to Applications > Accessories > Console (or Terminal)
-run ```
sudo gedit /etc/modprobe.d/blacklist.conf
```

-add this to the end of the file and save```
blacklist pcspkr
blacklist snd_pcsp
```

-run ```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

-and add the same lines to the end of the file, save and reboot.```
blacklist pcspkr
blacklist snd_pcsp
```

It should disable every kind of system beep in the computer.

---

### Post by rpz79 on 2009-12-21
It's not a system beep and I don't have "Play alert sounds" checkbox
in sound preferences.
I've of course tried the second gedit option with no avail.
What happens to the OS when the sound preferences screen is in background ??
With other screens it doesn't work and like I've said before when the HDD is in action (you can hear him) this buzzy voice quietens.
I hope you can still help me find the solution.

:-({|=
A BEAST OF DIFFERENT KIND

---

