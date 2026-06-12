---
title: "Oh goodness! Could someone help me out with my mouse?"
date: 2009-03-01
forum: Hardware
---

### Post by dietcola on 2009-03-01
I've searched this forum (and the internets) yet have yet to find an answer (most of the threads were old, anyways).

Here's my problem, explained to the best of my ability:

In Windows, there are two main mouse settings: sensitivity and acceleration.

*Sensitivity:* Sensitivity determines how far the cursor moves in relation to how far you move the mouse. Essentially, sensitivity is the "speed" of the cursor.

*Acceleration:* This one is more difficult to explain. Sensitivity is roughly the rate at which the cursor's speed increases the longer you move the mouse without slowing it down. In other words, if you move the mouse at a constant one-inch-per-second, the longer you move the mouse, the faster the cursor moves (assuming acceleration is enabled).

A high number computer gamers disable acceleration. When playing a game, you expect the mouse-to-cursor relationship to be constant, not variable, so it really helps to disable it. I'm one of those gamers!

I'm trying to do the same in Ubuntu (which I just installed).

However, it seems acceleration and sensitivity have different meanings! When I completely disable acceleration, and I actually experience **deceleration**. In fact, changing sensitivity seems to have little effect on anything! Apparently, I'm not alone in this, but so far, I've yet to find an answer.

I want my mouse to have high windows-sensitivity and zero windows-acceleration. Is there some file I should edit to accomplish this?

Thank you for your time.

---

### Post by trapgate on 2009-03-01
These settings are in the gnome mouse preferences (System/Preferences/Mouse) in Ubuntu 8.10. The only catch is that the mouse sensitivity has the opposite sense from what you're used to - setting it very low will make the cursor move a lot for a little mouse movement.

8.10 may be the first version where both of these settings are in the settings gui, I can't remember now.

---

### Post by dietcola on 2009-03-01
It seems "xset m 1 1" works, but I have to do it every time my computer starts. Is there a way to automate this?

---

### Post by kavon89 on 2009-03-01
> **dietcola said:**
> It seems "xset m 1 1" works, but I have to do it every time my computer starts. Is there a way to automate this?

That command turns off mouse acceleration. (Which is optimal for gamers).

You can either edit /etc/rc.local with your command or go to System -> Preferences -> Sessions and Add the command there.

---

### Post by dietcola on 2009-03-01
kavon89, thank you for your response.

Being new to all of this, I'm not quite sure what you mean by "/etc/rc.local".

I see the following similar folders:
/etc/rc0.d/
/etc/rc1.d
[...2-5...]
/etc/rc6.d
/etc/rcS.d

What does "rc" mean and where is the file/folder you mentioned?

---

### Post by kavon89 on 2009-03-02
I'm pretty sure you need to do this as root and with the command line.

```

cd /etc

gksudo gedit rc.local

```

Those two commands (in order of course) will open up your rc.local file. Paste your command on a new line above the "exit 0" and hit save. Then reboot and it should have executed it on boot.

---

