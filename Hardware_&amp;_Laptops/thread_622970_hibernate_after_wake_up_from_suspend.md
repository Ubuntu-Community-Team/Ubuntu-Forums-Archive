---
title: "hibernate after wake up from suspend"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by dmitryf on 2007-11-25
Hello!  Laptop going to hibernate after succsessfully wake up from auto (after one hour)  suspend (after entering a password). If i force going to suspend by myself - everething is ok.

Thanks!

---

### Post by Peturrr on 2008-03-07
I am having the exact same issue on my desktop. Did you find a fix for it?

---

### Post by Peturrr on 2008-03-11
I think I found a solution to this weird problem.

It looks like gnome-power-manager has two options, one is available as a setting in the menu, the other one is only available in the gconf-editor.In the gpm settings dialog, you can set the PC's timeout for initiating hibernate. However, there is also an option in the gconf-editor for gpm, that handles the sleep timeout. In my fresh install of Ubuntu, I putted the hibernate function on 11minutes, and the sleep function appears to be setted at 120 seconds. 

Probably this is going wrong: after 120 seconds, the PC starts sleep mode. When you start it again, it somehow makes the error that the 11 minutes have also passed and thus hibernating needs to be activated.I now have put hibernation to off, and sleep to 180s, will report later if this seems to be working.

Still, this is really a weird bug. I also wonder why sleep cannot be configured from the settings menu of gnome-power-manager...

---

