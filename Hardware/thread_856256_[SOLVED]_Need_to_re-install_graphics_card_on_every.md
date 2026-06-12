---
title: "[SOLVED] Need to re-install graphics card on every boot"
date: 2008-07-11
forum: Hardware
---

### Post by Ephemeral on 2008-07-11
Hello hello,

I have recently been encountering a problem, everytime I boot Ubuntu I need to re-install the drivers for my graphics card, on boot I get a little message, about screen resolution and it seems no drivers are installed anymore.

To install my graphics card I usually do this :

```
CTRL+ALT+F2
*log in*
sudo /etc/init.d/gdm stop
cd /home/eternal/Desktop/
sudo sh Graphics.run

sudo /etc/init.d/gdm start
```

But this time, my screen went black after I pressed CTRL+ALT+F2, no command line, nothing.

Any ideas?

Cheers,
Eph

---

### Post by Ephemeral on 2008-07-11
Three page bump**

---

### Post by Ephemeral on 2008-07-13
Bump again

---

### Post by sdennie on 2008-07-13
Is it an nvidia graphics card?  If so, try this thread: [http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2](http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2)

---

### Post by Ephemeral on 2008-07-14
Thanks a lot mate, works fine now :)

---

