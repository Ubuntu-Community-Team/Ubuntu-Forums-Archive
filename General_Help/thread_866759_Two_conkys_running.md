---
title: "Two conkys running"
date: 2008-07-22
forum: General Help
---

### Post by Foxblood on 2008-07-22
Hi, All,

On a normal start  get two Conkys running. Towards the end of the normal boot process I get a Conky that flashes briefly then disappears. Awn comes out and then Conky appears properly. If I try to continue normal use I get a square in the upper left of my screen that overwrites any open windows. According to System monitor, I have Conky running twice along with the Conky script that makes Conky wait twenty seconds before starting. If I use System Monitor to kill the first instance everything returns to normal. I've spent quite some time trying to resolve this but I can't figure out how the first instance starts. It's not in Sessions or anywhere else I could think of to look. How can I prevent the first Conky from starting?

---

### Post by kidux on 2008-07-22
Where in sessions did you look? Did you check the current sessions tab?

I was having a similar problem, and what I did was go through the session manager and kill everything I didn't want running, then closed all programs I didn't want to run at boot, then clicked for it to save session on exit, then logged out and back in, which fixed the problem. You might try that, just remember to uncheck that box after you get it the way you want.

---

### Post by Foxblood on 2008-07-22
I blush to admit that I figured it out - I had two Conky startup scripts in my home. That's why the problem was so persistent. Thanks for your effort.

---

### Post by dannyboy79 on 2009-02-23
i know this thread is old but I too am having this issue and conky takes a lot of memory to run. I only have 1 conky script in my /home/user directory so that's not it.

I did a ```
ls -la | grep conky
```
and it returned these 3 things:
-rwxr-xr-x  1 daniel daniel       37 2008-01-04 19:04 .conkylaunch
-rw-r--r--  1 daniel daniel     3616 2008-02-13 17:24 .conkyrc
-rw-r--r--  1 daniel daniel     3939 2008-02-13 17:23 .conkyrc~

.conkylaunch contains this:
#!/bin/bash
sleep 20 &&
conky &
exit

the other 2 files contains the config settings for conky, or at least I thought they did?

Can anyone help with this?

---

