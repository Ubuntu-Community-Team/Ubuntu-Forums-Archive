---
title: "Samsung NP305v5a-a05us Touchpad Issues"
date: 2012-04-07
forum: Hardware
---

### Post by adamluck on 2012-04-07
Hello,

I have a Samsung NP305v5a-a05us on which I've installed Ubuntu 11.10.  It works well except for one nagging issue: the touchpad response is terrible.  In order to even move the mouse it requires me to put a lot of skin on the surface of my pad and the touchpad is unaffected by the settings that I change in the settings manager.  In another post ([http://ubuntuforums.org/showthread.php?t=1939067&highlight=np305v5a-a05us]("http://ubuntuforums.org/showthread.php?t=1939067&highlight=np305v5a-a05us")) I found after executing these two commands my tracking issues were dispelled.
```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps 
```
However, the touchpad completely disappears in the settings manager and I cannot scroll with the two-fingered scroll that I was able to use before I executed those commands.

Is there a way to both fix my tracking issues and also retain the two-fingered scrolling?

Thanks in advance!

---

