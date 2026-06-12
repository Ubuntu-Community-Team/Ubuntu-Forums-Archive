---
title: "POssible to restart buggy trackpad driver without rebooting?"
date: 2011-12-08
forum: Hardware
---

### Post by blackbird34 on 2011-12-08
Hi 
Every so often, usually after several hours work or if i put my laptop on my lap (the irony...), my trackpad starts malfunctioning. It seeems to be random, and the return to normal seems to be random too. Its not serious because i ca n do almost everything with the keyboard if necessary, but if it's persistent, is there a way of restarting the trackpad driver or something to clear the problem? Because if it annoys me, i can just reboot, and it all goes back to normal, but that takes a minute or two...

Buggy trackpad symptoms : erratic movement, cursor refusing to go sideways and will only go up and down, touching the trackpad can do a right click (which isnt what i configured in mouse preferences), ...

Hardware: Compaq Presario CQ56 133-SF, bought this year. Ubuntu 11.04.

---

### Post by blackbird34 on 2011-12-17
bump.

---

### Post by 2F4U on 2011-12-17
Did you try to just logout and back in?

---

### Post by blackbird34 on 2011-12-20
Thanks. I hadn't, because the logout menu doesn't function for some reason. In the end i just learnt the command:

gnome-session-save --logout
OR:
gnome-session-save --force-logout

(Ubuntu Natty w/Gnome Classic)

---

### Post by mickymills on 2012-09-02
I am having a similar problem with my Presario CQ62. I am trying to reproduce the problem while watching the log files to get an insight into what is going on.
Can anyone tell me the log file that a module will output to if it is complaining?
):P

---

