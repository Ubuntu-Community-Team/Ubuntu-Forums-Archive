---
title: "Revert to Intrepid?"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by pmurphydc on 2009-03-29
I'm having multiple issues after updating to Jaunty Beta. I'm having difficulty launching ANY applications. Instead of fixing this, I'd rather revert to Intrepid until the final release of Jaunty comes out next month. I can still access terminal. Is there anything I can enter to revert to Intrepid? I don't have another computer with me to download Intrepid again. Any help would be appreciated!

---

### Post by cariboo on 2009-03-29
The only way to revert to a previous version is to do a clean install. It sounds like you got bit  by the python bug mentioned [here]("http://ubuntuforums.org/showthread.php?t=1107854"). The way to repair the problem is to open a terminal and type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Jim

---

### Post by pmurphydc on 2009-03-29
That appears to have done the trick! Thank you much.

---

