---
title: "upgrade froze on executing dkms"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by roboa1983 on 2009-08-22
Hello:
For the last months I have had trouble updating my machine (amd-64 bit, currently with 8.10). Every time I tried to use synaptic or apt-get, I got a hang on the following section.
```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms

```

Looking online, it seems it is an nvidia-common problem. However, it is impossible to finish purging or installing something as the last step is the one above and it crashes.

I tried to do a system update, to try to circunvent this situation, but to no avail. As of right now, I have the same hang. It also seems the processors are not doing too much.

Any idea how to get the installation to stop without causing more pain, and also how to purge something without the use of synaptic/apt-get?

Thanks!

---

### Post by roboa1983 on 2009-08-23
As an update, the update hung on the same stage. I cannot do any sort of updates without overriding this stage.
Any hints, ideas? I know for sure I exhausted all of them.

Thanks!

---

