---
title: "Job on certain tty with upstart"
date: 2008-08-01
forum: General Help
---

### Post by izo_86 on 2008-08-01
Hi there,

I have some problems concerning upstart in ubuntu which replaces the /sbin/init known from Debian. I have gdm as default-display-manager, but I need another one that runs parallel so I can switch between the two via ctrl+alt+#.
On Debian I did this via inittab

7:2345:respawn:/usr/sbin/gdm -- :0 
8:2345:respawn:/usr/lib/ltsp/screen.d/ldm

I can start the ldm DM manually on tty8 and that works fine. But I'd like to have it automatically, when ubuntu starts up. It is supposed to run on tty8 (created in in /etc/event.d)

if anybody knows how to make this working with upstart, that would be awesome.
thank you!

---

