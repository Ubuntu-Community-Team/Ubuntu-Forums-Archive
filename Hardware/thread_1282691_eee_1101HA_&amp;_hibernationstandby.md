---
title: "eee 1101HA &amp; hibernation/standby"
date: 2009-10-04
forum: Hardware
---

### Post by badook on 2009-10-04
Hi, I'm trying to set up ubuntu on a asus eee pc 1101HA, and I can't say it's been easy, however I did manage to solve most problems. One thing I can't fix is resuming from hibernation/standby.
When resuming from hibernation I get these two messages:
```
drm_sysfs_suspend
```
and
```
assuming drive cache: write through
```

When trying to resume from standby the screen goes black.

Both times the only way to restart is using alt+sysrq+b keys

I also tried to add to 
```
"/usr/lib/pm-utils/defaults" 
SUSPEND_MODULES="uvcvideo"
```

I hope someone of you Linux geniuses has already faced and resolved the problem, thanks in advance!

---

### Post by badook on 2009-10-05
*bump*

---

### Post by badook on 2009-10-06
Please! nobody else has this problem?

---

### Post by Adavur on 2009-10-06
Well, this seems to be a well known problem. I own an 1101HA too, but right know I am trying to figure out the screen resolution. Did you fix that?

---

### Post by badook on 2009-10-09
I just followed this guide: [http://ubuntuforums.org/showthread.php?t=1229345&highlight=gma+500]("http://ubuntuforums.org/showthread.php?t=1229345&highlight=gma+500")

---

### Post by keberjan on 2010-02-26
Hi! I have 1101HA too. I managed to fix resolution with the same tutorial that you used. And after installing those GMA 500 drivers standby is not working anymore.

---

