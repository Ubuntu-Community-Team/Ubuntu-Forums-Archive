---
title: "laptop fan"
date: 2008-09-07
forum: Hardware
---

### Post by kennedy7 on 2008-09-07
Im running Ubuntu 8.04 on an Everex VA1500V. What i need help with is my laptop fan is on all the time. But when i take it off of suspend my fan works right. Basicaly what is happening is it doesnt work unless i put it on suspend amd then take it off. If i dont do that then the fan is on all the time. Any help.

---

### Post by starcannon on 2008-09-07
sounds like a module isn't loading at boot time, and is getting loaded by the resume script.

Perhaps look at the resume script see if you can discern whats loading up that isn't loading at boot.

Then either add the module to /etc/modules
Or make your own boot script, heres a nice mini guide on that:
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

Thats how I'd go about it anyway.

GL

---

### Post by kennedy7 on 2008-09-09
Thanks but it didnt work for me. I put the original system gOS on my everex VA1500V but the fan still runs all the time and does the suspend thing. Still no luck.:popcorn:

---

