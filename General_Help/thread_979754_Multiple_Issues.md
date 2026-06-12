---
title: "Multiple Issues"
date: 2008-11-12
forum: General Help
---

### Post by Gnu32 on 2008-11-12
Greetings, I have a few problems that I can't seem to find the right solutions for and search seems to come up with nothing!

[COLOR="Gray"]First off, much to my horror and suprise, I've discovered that after upgrading to Ibex the PC Beep/Speaker had been re-enabled. I've tried the solution of using "modprobe -r pcspkr" and added "blacklist pcspkr" to the blacklist but the pc speaker is still enabled and beeping when using console mode.[/COLOR]

Second, another upgrade issue, GNOME seems to be rejecting rox-filer as a default file manager. Specifically, even with the instructions [here]("http://roscidus.com/desktop/Ubuntu")* and [here]("http://ubuntuforums.org/showthread.php?t=48169") it simply does not load rox-filer on startup nor register file:\\ protocols with it.

Finally, IIRC, Ubuntu has (or used to have) a graphical startup in which the scrolling text (ie. Setting system clock... [done]) would be shown in a box under the ubuntu logo instead of full screen. I'd prefer it this way but never had it so, perhaps due to initially installing Xubuntu and then transitioning to Ubuntu via package manager. Does this graphical bootup still exist? If so, how can I get it back?

Cheers (for reading my essay :P)

* in this tutorial, one of the steps is to set nautalis as "Deleted-items" in the "Sessions" settings panel. However the "Current Session" tab is missing... where can I find it? perhaps this is the key.

---

### Post by Gnu32 on 2008-11-14
A-ha, figured out the system beep.

Ibex seems to have introduced new "audio devices", as I noticed in the Sound panel that there are ALSA and OSS devices for "Internal PC-Speaker". Seems like they kept the PC Beep enabled.

To fix this, I went into Volume Controls and went to the ALSA "Internal PC-Speaker" device in the drop down menu and muted the slider for MASTER. In the Switches tab I unticked "PC Speaker". I did the same for the OSS "Internal PC-Speaker" (although there is no switch for PC Speaker).

This finally killed the annoying shutdown beep as well as bells in console.

---

### Post by Gnu32 on 2008-11-14
Ah, another problem has popped up :x

Magic SysRQ keys don't seem to work anymore. There I am continually hitting ALT+PRNTSCRN+B while Firefox does its usual thing of swapping memory all the time and nothing happens.

Again, this is post-upgrade. Before I could sucessfully and instantly execute ALT+PRNTSCRN+REISUB.

---

### Post by m4fia on 2008-11-14
Did the command change? Did they take it away?

---

