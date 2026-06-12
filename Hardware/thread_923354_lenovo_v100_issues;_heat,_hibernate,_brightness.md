---
title: "lenovo v100 issues; heat, hibernate, brightness"
date: 2008-09-18
forum: Hardware
---

### Post by mistlur1 on 2008-09-18
Hi

I'm running Ubuntu 8.04 on a lenovo v100 0763-3MG. It's not a bad experience, but there are some things that doesn't quite work. If you have any ideas about possible solutions I'd love to hear.

One quite serious issue is that when i hibernate the machine and wake it up, the fan starts to misbehave. I've found no way to control the fan, there seems to be no sensors recegnized, and after waking the machine the fan doesn't spin up at 68 degrees C (cpu) as usual and sometimes it doesn't spin up at all, bringing cpu temperature up above 80 degrees (at which i reboot). The only hint I've got is this entry in /var/log/messages:
```
gnome-power-manager: (christian) hibernate failed
```

Another not so serious but still annoying issue is that screen brightness keeps changing every boot (too dark) and every time a video file is played by vlc or mplayer the brightness automatically get changed (darkened).

Any pointers?

/mistlur

---

### Post by josvanr on 2008-09-25
same here on packard bell bg46

josvanr

---

### Post by Lord Xeb on 2008-09-25
It is an ACPI probelm.

maybe this will help: [http://www.thinkwiki.org/wiki/TuxOnIce](http://www.thinkwiki.org/wiki/TuxOnIce)

---

