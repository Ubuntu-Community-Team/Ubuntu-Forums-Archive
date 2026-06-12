---
title: "Intermittent shutdown failure."
date: 2010-01-31
forum: Hardware
---

### Post by slack on 2010-01-31
I clean installed Kubuntu 9.04 on a Sony Vaio VGN-BZ21VN and everything worked fine.  On upgrading to 9.10, however, the machine now intermittently won't shut down.  It goes through all of the usual steps but fails to power down at the end.  It hasn't frozen, I am still able to turn the power off with Alt-SysRq-o but if I do that the hard drive isn't cleanly unmounted.

Google suggested I try acpi=force as a kernel parameter in the grub config, or unload kernel module snd_hda_intel (I do have an Intel sound card) during shutdown.  Neither of these had any effect.

So far it hasn't ever done this whilst restarting, only shutting down, but as I said it's intermittent and I don't restart very often.

Here's an example of the final text on the screen when it happens (forgive any copy-typing errors, don't know of a way to export it):

```
init: tty4 main process (1136) killed by TERM signal
init: rsyslog-kmsg main process (857) killed by TERM signal
init: tty5 main process (1150) killed by TERM signal
init: cron main process (1184) killed by TERM signal
acpid: exiting
init: tty2 main process (1175) killed by TERM signal
init: tty3 main process (1176) killed by TERM signal
init: tty6 main process (1178) killed by TERM signal
init: tty1 main process (1824) killed by TERM signal
init: hal main process (993) terminated with status 1
init: avahi-daemon main process (925) terminated with status 255
init: statd main process (19437) killed by KILL signal
init: statd main process ended, respawning
```

Any help gratefully received -- let me know any other information I can usefully provide.

---

