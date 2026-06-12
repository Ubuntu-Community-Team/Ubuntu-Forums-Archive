---
title: "[SOLVED] Can't Fix Keyboard Auto-Repeat Feature"
date: 2008-12-06
forum: Hardware
---

### Post by rich1939 on 2008-12-06
RE: Ubuntu 8.10

No doubt I'm a noob---but I've messed around with the sliders in the System:Keyboard app, but even with a long delay I'm getting a lot a repeated keystrokes that I have to delete. I know that I'm getting pretty old and that my touch-typing isn't as fast as it used to be, but, even so, I would think that I could somehow obtain a longer delay than what the slider offers (I still want to be able to repeat keys, but only when I want to).

Of course, I can disable the repeat capability entirely in the System:Keyboard app, but I'd rather keep that ability for when I need it. Any suggestions would be appreciated.

---

### Post by rich1939 on 2008-12-06
**Bump**

What I meant for the title to say was that the keyboard repeat delay on my Laptop is too short, even when the System:Keyboard slider is set to the LONG position.

Is there a System parameter that I can change (how to do so?) to make the delay a bit longer, so that my (slow to lift) fingers don't create multiple repeats of the character I'm pressing?

Thanks in advance for any suggestions.

---

### Post by ridgeland on 2008-12-13
I had the same problem.
Here is my fix:
per this site
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/264196/comments/26](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/264196/comments/26)
I added 
kbdrate -r 25 -d 500
to the file /etc/rc.local
Now I can control the delay before repeat starts.  That's the ms after the -d option.  The -r gives the repeat rate 25/second.
I tried gconf-editor but like the keyboard GUI it didn't seem to change anything.

---

### Post by rich1939 on 2008-12-19
> **ridgeland said:**
> I had the same problem.
Here is my fix:
I added 
kbdrate -r 25 -d 500
to the file /etc/rc.local
Now I can control the delay before repeat starts.  That's the ms after the -d option.  The -r gives the repeat rate 25/second.
I tried gconf-editor but like the keyboard GUI it didn't seem to change anything.

Thanks very much for your reply. Sorry for my delay in responding. I appreciate you and everyone who contributes to these forums.

---

