---
title: "Log file for boot procedure."
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by Mr Green on 2006-06-07
I have a problem when booting Ubuntu nowadays. It hangs A LONG time when "Loading hardware drivers" and eventually it fails. 

I'm not sure what causes this but I suspect it appeared after I plugged a microphone into the soundcard???

Is there a log file I can look at to see which hardware driver fails?

---

### Post by soonindallas on 2006-06-07
try looking at dmesg:

```
cat /var/log/dmesg | more
```

or use the log viewer: system>administration>system log and choose dmesg

---

### Post by Mr Green on 2006-06-08
I did it the "easy" way. Popped in the Dapper cd and reinstalled it.

And with /home on it's own partition that was totally painless.

---

