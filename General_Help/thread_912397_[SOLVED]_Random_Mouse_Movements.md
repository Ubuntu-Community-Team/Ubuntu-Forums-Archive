---
title: "[SOLVED] Random Mouse Movements"
date: 2008-09-06
forum: General Help
---

### Post by nazgul42 on 2008-09-06
I am running Ubuntu with Gnome, and have the Compiz Fusion that I installed from compiz-git.  When I am just using the computer for about anything, every once and a while my mouse moves around the screen seemingly randomly, and I have no control over the mouse.  This lasts for about 10 seconds, and then the mouse goes back to normal.  During those ten seconds, new tabs are opened in Firefox/Swiftfox, and those tabs are opened to web pages, I think that it clicked on the stumbleupon button...  It also goes forwards and backwards in my browser history.  It also changes what virtual desktop I am on, and I see the rotating cube effect, so it seems like it might be affecting the keyboard, too.  This has not caused any actual damage or loss of data, but it happens just often enough to be extremely annoying.  It happens most often when I am using firefox/swiftfox, but it happens when I am using other applications as well.  I have just installed Ubuntu earlier this week.  Any help with this would be greatly appreciated.

---

### Post by txcrackers on 2008-09-06
Are you on a laptop and do you have a habit of resting your hands on the case near the touchpad? If so, you're probably slightly warping the case and causing the touchpad to send erroneous signals - and lots of them (hence the apparent non-responsiveness - your computer's busy taking care of the backlog of events).

---

### Post by nazgul42 on 2008-09-06
No, I am not on a laptop.  I saw that on different forums, but it didn't help.

---

### Post by Shazaam on 2008-09-06
Sounds odd to me. Does it look like a live person is moving the mouse? Does it go through the exact same moves each time (like a demo)?
Unplug/change the mouse. Try to see if it happens again.

---

### Post by nazgul42 on 2008-09-07
No, it doesn't look like a live person is controlling the mouse, and it probably isn't a demo, because it doesn't seem to do the same thing every time.  It moves all over the screen, and sometimes while it's doing that, I can move the pointer left and right, and sometimes that affects things (like switching virtual desktops without me pressing anything), but most of the time it doesn't.  I tried unplugging and plugging my mouse back in, but that doesn't help.  It might be a hardware error, but I have had this mouse for more than 6 years, and it hasn't done anything like this before.

---

### Post by Shazaam on 2008-09-07
Hmm. How is your mouse listed in /etc/X11/xorg.conf? You don't need to post the whole thing here, just the part about the mouse.

---

### Post by txcrackers on 2008-09-07
> **nazgul42 said:**
> It might be a hardware error, but I have had this mouse for more than 6 years, and it hasn't done anything like this before.

I've never had a mouse last that long. I would sincerely suggest replacing the mouse or at least swapping with a friend or something. Because it's intermittent, the mouse itself is so old, and seems to have just started happening, I'd bet on hardware...

---

### Post by nazgul42 on 2008-09-07
I have not touched the mouse section of xorg.conf, but here it is:
```
Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```
I think that getting a new mouse would probably be good, but I doubt that I will be able to if I can fix it some other way.

---

### Post by nazgul42 on 2008-09-07
This also happens if I disable networking, so it isn't something controlling my mouse from the internet or something...

---

### Post by nazgul42 on 2008-09-09
OK, I have determined that it was a hardware issue, and a new mouse fixed the problem.

---

