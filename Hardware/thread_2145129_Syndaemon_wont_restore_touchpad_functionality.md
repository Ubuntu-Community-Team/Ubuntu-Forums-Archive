---
title: "Syndaemon wont restore touchpad functionality"
date: 2013-05-14
forum: Hardware
---

### Post by dajhull on 2013-05-14
Hi all, I've searched for a solution to this, but nothing seems to work. Any advice would be realy appreciated. I'm trying to use syndaemon to prevent touchpad  tap-clicks while I'm typing. For example, I used the command 

```
syndaemon -t -i 1 
``` 

which is supposed to disable tapping while typing, with a one-second delay until tapping is restored. 

Syndaemon disables tapping just fine (which is better than the GUI touchpad settings thing) but tapping is not restored at all. Even when I enter

```
kill syndaemon
```

or

```
killall syndaemon
```

tapping still doesn't work, and the only way to restore it is to log out and log back in again. To be clear, I can still move the cursor and click with the buttons, but that's quite a pain. I'm using Ubuntu 12:10 with Gnomeshell. I don't know how to detect my touchpad model, but the computer is a Samsung Series 5 NP530. 

Thanks in advance for any advice!

---

