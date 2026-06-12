---
title: "x11 over SSH"
date: 2008-10-20
forum: General Help
---

### Post by theevilhamster on 2008-10-20
As I have said in other posts, I use SSH a lot (mainly form my ipod touch to my laptop). I want to run mplayer so it shows up on my laptops x11 display, but when I run it I get no picture. When I try to run another program like firefox, it asks me for a display. How do I tell mplayer to use the x display on my laptop?

my output of ```
echo $DISPLAY
``` is :0.0

Thanks a lot!

---

### Post by Sam on 2008-10-20
You want to execute commands remotely and get the windows to your pc ?

This way use X11 forwarding:
```
ssh -X user@host
```

Then run any command in the ssh session, eg:
```
gedit
```

gedit will run on the host but displayed on your pc.

---

### Post by Dr Small on 2008-10-20
So, you want mplayer to load on the X display of your laptop while SSHing from a remote computer? If so, you don't want to use the -X switch, but instead, set the display properly.

First, SSH in as normal, then run:
```
export DISPLAY=:0
```

Now run:
```
mplayer&
```

mplayer should now run on the laptop's display.

---

### Post by theevilhamster on 2008-10-20
Thanks guys, will try this when I log back into ubuntu, having problems at the moment:(.

---

### Post by theevilhamster on 2008-10-21
huummm I just get
"no protocol specified
cannot open display :0.0"
any more ideas?
thanks!:confused:

---

