---
title: "unregister-net device error (warning) doesn't allow sleep or hibernate Inspiron 6400"
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by arthur_kalm on 2006-10-10
Hi everyone,

I recently got a new Dell Inspiron 6400 and so far it's been awesome. XGL/Beryl works very well on the x1400 and sleep and hibernate used to work without any problems. However, recently I haven't been able to put my laptop to sleep or hibernate it at all. Here are the chain of events that occur:
[LIST=1]
[*]Put laptop to sleep (or hibernate)
[*]close the lid and notice that it's still running after a few minutes
[*]I open the lid and it lets me log in
[*]I can't run any commands what so ever (any programs or turn off the computer). The menus work and so do the programs running, however, trying to launch something new, it doesn't work
[*]I end up having to turn off the computer with the button.
[/LIST]

When this occured once (before I shutdown), I went to the terminal (Ctrl + Alt + 1) and noticed that something kept on being printed there:

```
unregister-net device: waiting for wlan0 to become free. Usage count = 1
```

When I saw this I tried to shut down wlan0 with ifdown, but as I said above, no commands work. When I say they don't work I mean that they freeze the terminal. I'm not able to even kill them with Ctrl + C (let alone using the kill command because it also freezes).

I'm very happy with the Dell Inspiron 6400 but I would really like for it to be able to sleep and hibernate again. Thank you in advance for any help you can provide.

P.S. I'm using the Broadcom bcmwl5 driver with ndiswrapper.

---

### Post by CoolkcaH on 2006-10-27
I have the same problem when I try to shutdown or hibernate I get the unregister netdevice error and have to hardreset the laptop.
It happens with a Intel ipw2200 on a Fujitsu P7010.

Even after I upgraded to Edgy it's still the same...

---

### Post by kinanti on 2006-10-29
Same problem here. Except that the screen remains entirely black after suspend.

K.

---

### Post by Ocxic on 2007-07-31
were having the same problem, but it related to ndiswrapper, seems he can suspend/hibernate while ndiswrapper module in loaded, and freezes every time i try to unload it.

---

