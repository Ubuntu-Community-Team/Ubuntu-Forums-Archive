---
title: "startup delay"
date: 2008-11-04
forum: General Help
---

### Post by tiberiup on 2008-11-04
Hi, when i login i must wait about 30 seconds for desktop...
I found some errors in /var/log/usr.log :
```

Nov  5 04:28:48 tibus-pc pulseaudio[6544]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  5 04:28:48 tibus-pc pulseaudio[6546]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  5 04:28:48 tibus-pc pulseaudio[6546]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  5 04:29:02 tibus-pc pulseaudio[6546]: module-x11-xsmp.c: X11 session manager not running.
Nov  5 04:29:02 tibus-pc pulseaudio[6546]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov  5 04:30:09 tibus-pc python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Nov  5 04:30:09 tibus-pc hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
```
I tried to uninstall pulseaudio with synaptic and i can't login in X, i reinstalled pulseaudio from console and now same delay same error... 
I have Ubuntu 8.10

---

### Post by tiberiup on 2008-11-05
Can anyone help me ?

---

