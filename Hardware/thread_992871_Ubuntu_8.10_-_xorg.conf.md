---
title: "Ubuntu 8.10 - xorg.conf?"
date: 2008-11-25
forum: Hardware
---

### Post by phil9r on 2008-11-25
Hello there,

I would like to change my graphicsdriver to i810 because my system is way to slow...
And I would like to do some other things ... BUT:
I can't find following files / lines:

/etc/X11/xorg.conf
----> Section "Graphic"
Or something like that.
I didn't find a "Section Layout" too.

/etc/inittab
I would like to configure Ctrl + Alt + Del
Where can I do that?

Best regards,
phil

---

### Post by davidbilla on 2008-11-25
System->Preferences->Keyboard Shortcuts for Ctrl+Alt+Del.

And, about xorg, you might have to look for Section 'Device'.

If your problem is solved, mark this thread as SOLVED. I'd like to know whether it worked. Because, I had (still have!) problems with my xorg.conf though this i810 part seems to be solved. And by the way, you might want to try 'xserver-xorg-video-intel' in Synaptic.

---

### Post by phil9r on 2008-11-25
Hey, didn't had time to test it - I will get back as soon as I tested it. (Tomorrow around 10 o'clock I think)

---

### Post by phil9r on 2008-11-26
Ok - tested in Section "Device" some times before - I wanted Linux to use i810.
After that, I couldn't start X, it had troubles using this Driver. I used it many times before (Debian usw...)...

---

