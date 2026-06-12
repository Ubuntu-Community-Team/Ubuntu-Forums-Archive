---
title: "Sysmonitor screenlet issue"
date: 2008-09-25
forum: General Help
---

### Post by Gilbum on 2008-09-25
Hi, I'm new to linux and have been playing with Ubuntu 8.04 for about 3 weeks now.  I think I have my desktop setup mostly to my liking but I'm having a problem with the sysmonitor screenlet that came with the OS.  Whenever I reboot (it's a laptop so reboots are frequent for me) my sysmon screenlet shows up kind of garbled.  The top section with the logo, date/time, user/distro/kernel version all show up fine but everything below is missing pixels.  I usually open up the screenlets daemon and click restart all screenlets and then everything looks good.  

the only other screenlet I'm running is the calendar and it runs fine.  Any thoughts on what might be causing this? I'm running screenlets 0.0.12.

Thanks.

---

### Post by loomsen on 2008-09-25
That's the most recent version, afaik the developers stopped working on screenlets quite some time ago.

However, first, it would be useful if you'd post maybe your ~/.gnome2/session(if you are using gnome) file here. My first thought would be that you're trying to start too many programs at startup at once. For example, I have a desktop-embedded-terminal. If I simply add it to my autostarters it just won't start where I specified it to start. Restarting it and it starts as if it never did sth else. So I wrote a skript to make it startup a little bit later than other services.

```

#!/bin/bash
sleep 10 && xfce4..... and the respective arguments.

```

Same for conky, sleep 20(about the time it takes me to enter my passwd to unlock my keyring) and start, and you can be quite sure it wont bother any other prog. If it still does, you maybe should consider getting rid of quite some stuff :)

Give it a try, and let me know if it helped.

---

### Post by Gilbum on 2008-09-25
That does sound plausible... but I'm not really running all that much. I'm not near my linux box atm, but your delaying method sounds useful even if it turns out to not be my problem.  

Where would I go about putting a script, and more importantly where could I find a guide for writing one?

Thanks.

---

