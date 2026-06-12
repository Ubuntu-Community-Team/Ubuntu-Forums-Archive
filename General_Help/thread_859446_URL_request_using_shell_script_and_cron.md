---
title: "URL request using shell script and cron"
date: 2008-07-14
forum: General Help
---

### Post by Bartee on 2008-07-14
I need to run a URL request every 5 minutes.

I think I would use curl in a shell script.

The shell script would be run by cron.

I am new, but learning quick.

Any examples of this would be helpful.

TIA...bartee...

---

### Post by RealPSL on 2008-07-16
You can use curl but you can also use wget

```
wget http://fly.srk.fer.hr/
```

The example is directly from the wget man pages.

---

