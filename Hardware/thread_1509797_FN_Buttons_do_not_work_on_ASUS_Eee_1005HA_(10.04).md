---
title: "FN Buttons do not work on ASUS Eee 1005HA (10.04)"
date: 2010-06-14
forum: Hardware
---

### Post by GammaQuantum on 2010-06-14
Hello,

I got the netbook version of Ubuntu 10.04 installed on my ASUS Eee 1005HA.

As announced in the wiki, some of the FN keys do not work properly. That would be like FN+F3 to disable the trackpad or FN+F[10-12] for the sound options.

Is there any way to fix that?

Please do not kill me, I have searched the web, but I found lots of different versions of Ubuntu and different versions of the Eee PC with different Buttons, so that did not really help me out.

Thanks for any suggestions!

---

### Post by barrieluv on 2010-06-16
Don't know about the NBR version, but the regular 10.04 (default install), with all updates applied gives me:

Fn+F1 Working (Suspend and return from Suspend)
Fn+F2 Working (Disable and re-enable WiFi)
Fn+F3 Working (Disable and re-enable touchpad) (The silver key, top left, also works for this)
Fn+F4 Don't know (what is it supposed to do?)
Fn+F5 & F6 Working, but no OSD (Brightness down and up)
Fn+F7 Don't know (what is it supposed to do?)
Fn+F8 Working (Switch external display)
Fn+F9 Not sure about this (I used Ubuntu-tweak to map the system monitor to this key)
Fn+F10, F11 & F12 Working with OSD (Volume mute, down and up)

Some of these didn't work on the initial install but updates seem to have fixed them.

---

### Post by GammaQuantum on 2010-06-16
The FN+F7 cuts the backlight of the display, that is pretty good when you just listen to music and do not want to burn the battery for the display.

So you would say that there is or will be an update fixing that? Could I just used "Ubuntu Tweak“*to set up all those buttons?

---

### Post by barrieluv on 2010-06-16
I honestly wouldn't know how to make the Fn+F7 combination turn off the display.  I'm sure some searching would throw up an answer to this. 
The Fn+F9 combination uses the gnome-system-monitor command to make it work.
As for updates, it just seems to be a case of wait and see.
You might want to take a look at Bornagainpenguin's guide on here or at the Eeeuser forum.

---

### Post by barrieluv on 2010-06-16
Okay, it's not perfect but it will do the job.  Found this lurking elsewhere on here.
Mapped the command 
```
xset dpms force suspend
```
to the F7 key.  
For some reason I can't get it to map to Fn+F7, but there's almost definitely a way to do that.

---

