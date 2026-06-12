---
title: "tty screens and window managers not taking up full desktop space?"
date: 2016-11-08
forum: Hardware
---

### Post by ashley-a on 2016-11-08
G'day!

I have an old IBM X41 tablet laptop that I have installed Lubuntu on, and it works brilliantly. Much snappier that XP, which it has been running for a good 10 years now.
Before installing Lubuntu, for an unknown reason, the screen died. I disassembled the laptop and removed the screen. I now use it with an external monitor. The BIOS is told to boot with the main display as the external monitor, and all is well.
Unfortunately, Openbox and tty1-7 only use a fraction of said external monitor's screen space. Here is an example (note that this is obviously not my setup. Just some clipart that I edited).

LXDE:

[[IMG]https://s4.postimg.org/8hgat325l/Lubuntu.png[/IMG]]("https://postimg.org/image/8hgat325l/")

TTY and Window Managers:

[[IMG]https://s17.postimg.org/ox9h9oq1n/TTY.png[/IMG]]("https://postimg.org/image/ox9h9oq1n/")

Notice how on TTY and Window Managers, the text (or windows) does not take up the complete available space? It only uses a fraction of the screen real-estate.
Some extra information I'll add, just in case it is important, is that my screen supports 1024x1080 at 60fps. I am running the screen through VGA (the only available port on both the screen and the computer).

Thanks in advance!

---

### Post by Enigma12 on 2016-11-09
Have you checked under Preferences - Monitor Settings to see if your 1024x1080 is supported, at least by your video card? Does that monitor space get filled with the desktop? 

I don't have a laptop-external monitor setup, so I cannot duplicate what you have, so only offered the above as hopefully helpful.

---

### Post by ashley-a on 2016-11-09
Thanks for the reply.
I have checked under preferences in LXDE. The display is running at 1024x1080 at 60.02 fps. And it does run perfectly fine in LXDE, MATE, etc.
On Openbox and the linux command line, it seems to run at a lower resolution. only a portion of the screen is used.
Is there any way of checking the screen resolution from tty1? I could find out what it is outputting that way, correct?

---

