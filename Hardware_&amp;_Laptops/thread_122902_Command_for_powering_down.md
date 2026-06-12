---
title: "Command for powering down"
date: 2006-01-28
forum: Hardware &amp; Laptops
---

### Post by halfvolle melk on 2006-01-28
Hi,

Is there a command for powering down? I recently bought a PC with a server board that doen't power down after pressing the powerbuttom. Pulling the powerplug will do this of course, but it doesn't seem to be the right way to me.

Thanks

---

### Post by spartas on 2006-01-28
```

sudo halt

```

---

### Post by halfvolle melk on 2006-01-28
Cool, thanks!

edit: hmm, it seems to get stuck on
[somenumbers, morenumbers] Powering down

---

### Post by tukuyomi on 2006-01-28
Did you try ```
sudo init 0
```?

---

### Post by halfvolle melk on 2006-01-28
Just tried it and seems to be stuck at the same point. Half way installing Ubuntu the CD is ejected and a reboot is performed. This it does. Oh well, it's old and probably half broken. Thanks for the suggestion though!

---

### Post by TecSoft on 2006-01-28
To restart do:
sudo shutdown -r now

To shutdown do:
sudo shutdwon -h now

---

### Post by halfvolle melk on 2006-01-28
Ok, I'll try things first thing tomorow. I pulled the powerplug again (and cant try it now), because it sounds like a diesel in neutral. Thanks for your reply!

---

