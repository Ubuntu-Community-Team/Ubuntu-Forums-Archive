---
title: "Fan speed increases when screen turns off"
date: 2012-04-28
forum: Hardware
---

### Post by mvmacd on 2012-04-28
My laptop's CPU fan speeds up a LOT when the screen turns off, as soon as I touch the mouse to turn the screen on, the fan goes back to normal.

What would be causing this?

Ubuntu 12.04, HP Pavillion DV6-1149wm

---

### Post by brainwash on 2012-04-29
Taking a look at the process activity, while your screen is turned off, might help to solve the problem:
```
top -d5 -i -b > top.txt
```

The output of top (only non-idle processes, batch mode) will be saved every 5sec to the file *top.txt* in your current working directory.

---

### Post by mvmacd on 2012-04-29
nice idea.. okay, I set the display to turn off after 1 minute so I wouldn't have to wait long. Here is the output:

[http://pastebin.com/De3Ly4rU](http://pastebin.com/De3Ly4rU)

looks like it is compiz?

edit: I should also say I just removed the fglrx driver in hopes it was the Proprietary driver causing the fan to speed up for no reason, but it didn't. =(  So I am now on the opensource driver.
strangely, Youtube plays better on the opensource driver.  here is the unity test:
```

matt: ~ $ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6520G
OpenGL version string:  4.2.11627 Compatibility Profile Context

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```

what do you think?

---

### Post by brainwash on 2012-04-29
Alright, there is already a bug report including a workaround for the proprietary driver:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860)

According to comment #16 the workaround might even improve the overall performance. :)

---

### Post by mvmacd on 2012-04-29
> **brainwash said:**
> Alright, there is already a bug report including a workaround for the proprietary driver:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860)

According to comment #16 the workaround might even improve the overall performance. :)

thank you!  I did the workaround and it only uses about 8 to 10 percent CPU, at least on the short-term test I did.  Hopefully when I leave it for hours or even overnight [running programs] it will do the same.

---

