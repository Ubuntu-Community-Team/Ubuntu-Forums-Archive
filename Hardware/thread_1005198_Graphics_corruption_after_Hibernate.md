---
title: "Graphics corruption after Hibernate"
date: 2008-12-08
forum: Hardware
---

### Post by DIGGER_NZ on 2008-12-08
Hi,
My Thinkpad T40 works great on Ubuntu 8.1 with one exception...

When I come out of Hibernate, I get slight graphics corruption sometimes on menus and such. It appears as an old CGA type colouring just around the outline of the menu. I have done some searching and haven't found anyone else with this issue.
Does anyone have any ideas?

Thanks

---

### Post by andreasis on 2008-12-08
I have no idea and seeing that you weren't able to find anyone else with this issue.... can you post your userlog and syslog (located in /var/log/) right after you come out of hibernation?

Can you confirm which graphic card you have, which driver you are using, and whether the driver is the latest one?

---

### Post by iponeverything on 2008-12-08
I am seeing this too with a IBM X30. The laptop won't be back for about a week -- when it comes back, I plan on trying some things from here:

 [http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html](http://people.freedesktop.org/~hughsient/quirk/quirk-suspend-index.html)

---

### Post by DIGGER_NZ on 2008-12-08
Thanks Andreasis,
I will have a look at this tonight when I get home.

---

### Post by DIGGER_NZ on 2008-12-09
Here is the log from my last un-hibernate:

Dec  8 19:02:35 david-laptop pulseaudio[5347]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec  8 19:02:35 david-laptop pulseaudio[5349]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec  8 19:02:35 david-laptop pulseaudio[5349]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec  8 19:03:01 david-laptop pulseaudio[5349]: module-x11-xsmp.c: X11 session manager not running.
Dec  8 19:03:01 david-laptop pulseaudio[5349]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Dec  8 19:04:15 david-laptop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Dec  8 19:04:16 david-laptop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1

Running ATI Radeon 7500 32MB
It's just running standard driver (whatever comes on Unbuntu) as it worked fine out of the box so I didn't see the need to change.

Thanks

---

