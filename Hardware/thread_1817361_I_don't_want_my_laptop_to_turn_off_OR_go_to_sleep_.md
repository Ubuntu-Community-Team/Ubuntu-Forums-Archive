---
title: "I don't want my laptop to turn off OR go to sleep when it thinks the battery is empty"
date: 2011-08-03
forum: Hardware
---

### Post by BeRoot ReBoot on 2011-08-03
So I have a bit of a problem - the battery sensor on my laptop is pretty accurate, it shows zero charge remaining when there's still around 25%. The thing is, I can't figure out how to tell ubuntu NOT to turn off or suspend it when it thinks it's out of charge, because those are the only two options on the power settings. I just want it to keep going until it actually runs out. How do I do that?

---

### Post by Beacon11 on 2011-08-03
What makes you say that there is still 25% remaining when the sensor reads zero?

---

### Post by realzippy on 2011-08-03
I wonder why you want this...
data loss,corrupt file system  ??

Anyway,here you go:

```
gconf-editor
```

apps-->gnomepowermanager-->actions
Change the value of critical battery to "nothing"

---

### Post by BeRoot ReBoot on 2011-08-03
> **Beacon11 said:**
> What makes you say that there is still 25% remaining when the sensor reads zero?

Because, after it turns itself off, I can turn it back on, the indicator says 0%, and it stays on for another 40-50 minutes.

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

