---
title: "disk spins-down too fast"
date: 2012-04-26
forum: Hardware
---

### Post by bucz on 2012-04-26
I use Ubuntu 12beta on Lenovo Z575. I noticed that the disk spins down very quickly, few seconds after the last operation. And when I am working, e.g. in the vim and write quite often, it spins-up and -down frequently, what is rather annoying (and causes the vim to freeze for a second...)

I used *hdparm * but it didn't change anything:

```
    hdparm -S 24 /dev/sda # 2 minutes standby time
```

and I see (and hear) that the disk is idle or working:
```

    hdparm -C /dev/sda
    drive state is: standby # when idle
    # or...
    drive state is: active/idle # when spinning

``` 

I have *laptop-mode-tools* already installed

---

