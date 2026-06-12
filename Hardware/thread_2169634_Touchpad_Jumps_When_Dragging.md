---
title: "Touchpad Jumps When Dragging"
date: 2013-08-22
forum: Hardware
---

### Post by PowerEdgeTech on 2013-08-22
I have a laptop with a Synaptics touchpad and when I click/drag a window, the cursor/window jumps all over the screen.  I can drag a little, but more than about a half-inch, and it goes crazy.

I have already checked settings in the Synaptiks app ... not sure what "locked drags" are, but there is no change when enabling/disabling it.

Anyone have some tips?  If not, I'm not sure I can use Ubuntu on it like this ... I can't lock the output screen in Eclipse, drag a window or file, etc.

Thanks.

Ubuntu 13.04

---

### Post by BuntuSeriously on 2013-08-22
Try this from a command prompt:

```
/usr/bin/synclient MaxTapTime=0
```

This'll disable tap-to-click on your system until the next reboot.  If it works for you, make an autostart script with the following single command line:

```
bash -c "/usr/bin/synclient MaxTapTime=0"
```

Do this via Settings Manager > Session and Startup > Application Autostart > Add

Hope this helps --

;)

---

### Post by PowerEdgeTech on 2013-08-23
That didn't help the jumping.  Even if it had, I'm not sure I could live without tapping :)

Any other ideas?

---

### Post by BuntuSeriously on 2013-08-23
I'd try

```
synclient -l
```

to get a list of values which you could tweak in place of MaxTapTime

(There are a good couple of dozen parameters in there which are yours for the tweaking.)

My guess is that your system was furnished from the manufacturer with a WinCrapplet which made up for some type of native hardware quirk by adjusting the input/operational params.  Ubuntu doesn't come with any way of telling what these issues might be; so it's just a matter of tweak-and-try in some cases (like this?).

Anyway, I'm sure it'll all come out in the wash for you here.  It's a great community; and the hardware section has a good selection of helpful joes ;)

Have a great day --

---

