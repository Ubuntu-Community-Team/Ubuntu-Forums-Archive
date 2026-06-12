---
title: "Ubuntu dist-upgrade froze halfway through installation. Can't boot."
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by dopefish7590 on 2009-10-31
Hey all, I decided to upgrade to the newest Ubuntu version before I would mess around with the video card drivers on my system... Halfway through, the installation froze, no recovery by [Ctrl]+[Alt]+[F1] so I could get to a console or anything, the mouse didn't move. I had to turn off the system. After trying to boot up the computer, it said that it failed to boot, and to either type in my root password for maintenance, or press Control-D to continue... [Ctrl]+[D] just brought up the message again, and after logging on as root, I tried to figure out how to fix the problem. I tried to apt-get dist-upgrade, but it said that thre were packages that were still pending. So I typed dpkg -configure -a, and it wouldn't let me install anything since my drive was mounted read only, so a quick mount /dev/sda5 / -oremount ficed this, then I installed the pending packages the same way I tried before (Except for winbind, and a few other packaged, cant remember them, but they weren't required for booting any Linux.), after a reboot, I had the same problem after a restart... apt-get dist-upgrade didn't work either. Any way to fix a failed install?

Thanks!

---

### Post by dopefish7590 on 2009-10-31
Bump...
Anyone?

---

### Post by dopefish7590 on 2009-10-31
Hm, looks like it's something to do with GRUB... I Googled the probem and found how to update GRUB, and it dawned on me, I never posted exactly what it said on my screen. :o (The solution I found was about grub-update, and it didn't work anyways.)

The following is a type-up of what my screen says.

```
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2535) terminated with status 1
General error mounting filesystems.
```

I guess the lack of posts is what I get for the lack of information I gave...

---

### Post by saffi on 2009-11-02
Happened to me too.

---

