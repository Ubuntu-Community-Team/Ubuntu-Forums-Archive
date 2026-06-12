---
title: "Ubuntu 15.10 - AMD FX 8150 8core, something doesn't seem right."
date: 2016-02-01
forum: Hardware
---

### Post by wayne32 on 2016-02-01
[ATTACH=CONFIG]267058[/ATTACH]

The CPU is 8 cores and you'll see a few cores say 100% - then other cores will say 1% does Linux need sort of hotfix like windows 7 did?

---

### Post by QIII on 2016-02-01
Please do not cut and paste large images into the body of your text.  We have members with slow connections or data limits.  Let them decide whether or not to view the entire image.

Use the attachment functionality provided by the "paper clip" button in the toolbar above the text entry box.

---

### Post by Christopher_Stayne on 2016-02-01
I cant say wether a hotfix is needed or not.

Its possible that there is a process that is hitting one core exclusively and taking it to 100% usage.  I would go through your process list and sort it by CPU usage to see if there is any one process using a lot of CPU time.

Otherwise if you havent done so recently, I would open up a terminal and run:

```
sudo apt-get update && apt-get upgrade && apt-get dist-upgrade.
```

This will make sure everything on your system is up to date.

That is all I have for you.

---

