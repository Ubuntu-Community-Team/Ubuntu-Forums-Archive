---
title: "FN+F4(screen output) on HP dv7"
date: 2010-04-30
forum: Hardware
---

### Post by Tenn lynx on 2010-04-30
Hey

Fn+F4, which is supposed to change the output from laptop screen to HDMI, is as of 10.04, no longer functional. I am not even sure ubuntu 9.10 enables this feature on my HP pavilion dv7 (nvidia M9600 GT), but one of the 9.X series does, because it was working just fine last year... maybe it's a driver issue(nvidia 195.36.15)? Anyway, is there a way to debug and test this or maybe even a fix out there?

Thanks

---

### Post by Tenn lynx on 2010-05-02
bump

---

### Post by Jackelope King on 2010-05-02
I'm having the exact same problem on an HP DV3500. All the other fn+ keystroke commands work fine, but I can't get it to switch screen outputs either. Same NVidia driver version as well.

---

### Post by Jackelope King on 2010-05-02
Update: No solution yet, but I tried installing the older NVidia Drivers (v173) without luck in resolving the fn+F4 toggle command.

However, I have been able to get an external monitor to come up through the NVidia X Server Settings program. A major kludge, but it gets the job done for now.

This looks like it's a Lucid thing, not an NVidia thing, at least as far as HP Laptops is concerned.

---

### Post by JustinR on 2010-05-02
On my computer its FN + F8 but what I have found is that for that to work sometimes the cable has to be plugged in when the computer is off, then boot it up, then press FN + F8 and it works.

Some graphics cards don't check constantly for new output connections.

---

### Post by Jackelope King on 2010-05-02
> **JustinR said:**
> On my computer its FN + F8 but what I have found is that for that to work sometimes the cable has to be plugged in when the computer is off, then boot it up, then press FN + F8 and it works.

Some graphics cards don't check constantly for new output connections.

I've tried this on my DV3500, and unfortunately, that's not doing it. Even when the external screen is plugged in from before I turn the machine on, NVidia is able to recognize it, but can't toggle through to it with fn+F4. 

Under 9.10, I was able to plug in my external screen at any time and toggle successfully at almost any time.

---

### Post by Jackelope King on 2010-05-04
A new and interesting wrinkle in the problem, one which I think might be solvable with editing keyboard shortcuts (if only I knew how to do that)...

When I hit the fn+F4 key combination, the computer seems to be interpreting this as a keystroke on the "p" key.

---

### Post by Voluntocracy on 2010-06-26
gnome-keybinding-properties is the command to edit keyboard shortcuts.
In that program, fn+f4 shows up as Mod4+P, and is unassigned.
So all we need now is the name of the program which switches video output!

gnome-display-properties is a program where you can switch video output.

---

