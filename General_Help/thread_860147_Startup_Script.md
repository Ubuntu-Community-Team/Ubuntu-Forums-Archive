---
title: "Startup Script"
date: 2008-07-15
forum: General Help
---

### Post by Candle Jack on 2008-07-15
I get this error at boot:
```
Starting mpd... [COLOR="Red"]FAILED[/COLOR]
```
because I uninstalled mpd but it didn't take it out of the boot script.

Where is the file that does all those SUCCESS/FAIL steps at boot up?

---

### Post by Candle Jack on 2008-07-15
Bump :rolleyes:

---

### Post by brian_p on 2008-07-15
> **Candle Jack said:**
> Bump :rolleyes:

Try /etc/init.d

Also try

```
sudo apt-get remove --purge mpd
```

 to get rid of it.

---

### Post by Candle Jack on 2008-07-16
That's it, thanks!:)

---

