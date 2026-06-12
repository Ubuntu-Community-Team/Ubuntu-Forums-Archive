---
title: "Strange problem with GeForce 7150M and nvidia-settings"
date: 2011-03-18
forum: Hardware
---

### Post by grabbindrivers on 2011-03-18
Afternoon all,

I'm running Ubuntu 10.10 and I've ran into a rather annoying, but not crippling, problem.

I can set everything in the nvidia-settings menu just fine and get my external VGA monitor working after a little bit of fighting with permissions and the hit-and-miss settings of it. I then always save my xorg.conf so I can theoretically maintain these settings.

The problem arises upon restarting my computer. 

I get booted into tty1 with the famous "No display" issue. No problem, all I do is copy my working non-nvidia-configured xorg.conf into the old one and everything is well and good EXCEPT once I do that I lose all my monitor settings. Then I have to go back and redo everything again.

It would appear that even though nvidia-settings appears to "work", it doesn't write valid information to the xorg which causes corruption. 

Does anyone know any way to fix this? It's beyond frustrating. I'm kind of tired of spending 10 minutes every morning reconfiguring my display.

---

### Post by grabbindrivers on 2011-03-19
Bump, hoping someone can help me.

---

### Post by varunendra on 2011-03-21
Are you using correct driver for your display?
See if this helps: [http://ubuntuforums.org/showthread.php?t=987162](http://ubuntuforums.org/showthread.php?t=987162)

---

