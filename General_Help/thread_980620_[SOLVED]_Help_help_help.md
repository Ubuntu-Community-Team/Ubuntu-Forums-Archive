---
title: "[SOLVED] Help help help"
date: 2008-11-13
forum: General Help
---

### Post by 4t0m1c_w07f on 2008-11-13
I booted up this morning and now I get this when I login:

> Could not update ICEauthority file /home/jared/.ICEauthority

and

> There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited status 256

After I click ok to both these then it just shows the background and I can't do anything...

Yesterday I had been going through the threads and found a thread related to the .dmrc issue and I did the fix for it which had to do with changing home folder permissions...

I am now in root user and seems to work but when I went into my home folder in nautilus, there were only 3 folders in there...

Please help me!

---

### Post by 4t0m1c_w07f on 2008-11-13
This sorted it out:

```
chown -Rc jared:jared /home/jared/
```

---

