---
title: "Lenovo Ideapad z575 won't resume from suspend"
date: 2012-08-26
forum: Hardware
---

### Post by klepto on 2012-08-26
Hey Linux lovers, 

Got a new laptop and everything so far besides this issue works out of the box. When my laptop goes to sleep and then I attempt to make it resume the screen stays black. There seems to be more than a few bug reports about it. 

I've google'd plenty of times and installed a few scrips here and there to no avail. Should install the fglrx ati drivers? I've installed them recently and it makes my desktop flake out. 

Thanks for the help, this problem is one I can't solve.

---

### Post by gdea73 on 2012-11-06
Same problem, would appreciate some assistance in troubleshooting this. I've seen this is a widespread problem across many laptops with the newer kernels, and I haven't seen a single solution so far. Wish these things would be noticed before that kernel was adapted by all major distributions.

---

### Post by u2nTu on 2012-11-09
Confirming this, ***backlight does remain off after resuming from suspend***.

Checked /usr/lib/pm-utils/video-quirks/20-video-quirk-pm-lenovo.quirkdb, but find no entry for the Mobility Radeon HD 6620G (would be listed as just '6620').

But also spent hours trying every possible combination of quirk options (given **[here]("http://manpages.ubuntu.com/manpages/precise/man8/pm-action.8.html")**) using pm-suspend. **No combination worked**.

Then found a thread on how **radeontool** (which is installed by default) could be used to manually overcome this problem. Thought I was nearly there. But radeontool refuses to run, throwing error "cannot find ctrl region."

Searching more on this has led to dead ends:
```
dpkg-query -L pm-utils | xargs grep radeontool
```turns up the file /usr/lib/pm-utils/sleep.d/99video, which indicates that radeontool is being used to control the backlight. But **radeontool doesn't run**.

The mind-blowing thing about this is that **hibernate works flawlessly**. So if the backlight can be turned on after a hibernate, then why not after a suspend?

Obviously need help from somebody who knows more about this than I do. (And who is less frustrated. :mad:

This problem is widespread, as gdea73 notes, so a solution here may help many others.


[SIZE=3]**UPDATE**[/SIZE]
A little more info for those who turn this up in a search:

The glitch is with the open-source display driver. In particular, it seems a check and reset of display state on/off is missing. What the proprietary FGLRX drivers use to turn the display back on after a suspend is unknown, but they work.

Many have found workarounds. These involve turning the display back on manually by either ACPI (through system firmware) or by accessing the display control register directly. Examples:
```
xset dpms force on             # ACPI
sudo vbetool dpms off          #  ""
<keyboard shortcuts>           #  ""
sudo setpci -s 00:01:0 F4.B=x  # Direct-set register, x=brightness
```
After a suspend, these methods are tried 'in the dark' (display is black). For many, one of them will magically turn the screen back on <see light shine down upon them from above>. That method is then written into a custom file added to the /etc/pm/sleep.d directory and, all is well. For them.

For us, none of the methods work. Giving up on this now, I've installed the FGLRX driver.

Only remaining trouble is sleep loss thinking about the non-open-source software on my laptop.


PS.  radeontool can be uninstalled. It doesn't do anything.

---

### Post by u2nTu on 2013-08-08
New post (second update) to liven-up this thread.

Found a clue in this ongoing mystery.

After resume from suspend and with the screen irrecoverably black:[INDENT]**if the system is then hibernated (typically by closing the lid), then upon resume from hibernate, the backlight is switched back on. (!)**
[/INDENT]
 
This is reproducible (**works 100% of the time**), and is the first workaround -- if one can call it that -- to return usability of the computer without a reboot. (Still too much trouble, though. FGLRX driver is a far better solution.)

So if someone can figure out what is happening in the boot sequence (on resume from hibernate) to turn the display on, then a good workaround to this problem should be a snap. ( :^o?? )
 Clearly, whatever command is doing the trick is not getting sent during a resume after suspend. Or maybe it's sent but blocked. Or...


Found this after totally borking the system and being forced to do a reinstall. (Caused by a repair after install of a crazy Brother printer driver, and even after 17 hours of attempted rescue -- to no avail.)

**Any of you gurus have an idea what the magic command is?**

---

