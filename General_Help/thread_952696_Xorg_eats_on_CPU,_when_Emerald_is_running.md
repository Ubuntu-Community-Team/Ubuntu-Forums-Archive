---
title: "Xorg eats on CPU, when Emerald is running"
date: 2008-10-19
forum: General Help
---

### Post by hawkbane47 on 2008-10-19
When I have emerald running, xorg takes up to 50% cpu sometimes.....my hardware is enough to run emerald and compiz fusion (8600gt and 2gb)...so I don't know what the problem is

Any suggestions?

---

### Post by loomsen on 2008-10-19
Enable debugging and look into your system log.

Same card here, no issues.

---

### Post by hawkbane47 on 2008-10-19
sorry to sound really noob, but how does one do that?

---

### Post by loomsen on 2008-10-19
OK, in compiz you've got a settings manager. Go there by typing 
[code]ccsm &[/ccsm] whereever you find sth to do so, terminal, alt+f2 doesnt matter. (the & would leave ccsm open if you closed the terminal et vice versa)

There you should have a plugin called debugg logger (under utility)

Check its box, go on doing what you do. You can specify what shall be logged. Be sure you don't log to much tho.

You will find your log under /tmp.

These files will most likely tell you if its actually emerald causing the problem, and if, then why.

Your other system logs you may want to take a look at are located in:
/var/log

Welcome to your computer :)

---

