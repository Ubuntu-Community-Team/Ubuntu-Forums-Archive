---
title: "Program startup help"
date: 2008-11-12
forum: General Help
---

### Post by Bofur on 2008-11-12
Hi, I've been having troubles starting up programs like pidgin and conky upon startup. I made the files in my home folder here are both codes:

```
#!/bin/bash
sleep 20 && conky;
```

```
#!/bin/bash
sleep 20 && pidgin;
```

After I made the files I went into Sessions and set them to start on startup yet they never do. Anyone have any ideas? Thanks.

---

### Post by Liviu-Theodor on 2008-11-12
Have you marked the files as executables?

---

### Post by Bofur on 2008-11-12
> **Liviu-Theodor said:**
> Have you marked the files as executables?
That did it. Thanks a bunch. One more thing however, in previous versions of Ubuntu I never had to mark them as executables, why is that?

---

### Post by Liviu-Theodor on 2008-11-12
Not sure why in previous versions of Ubuntu you didn't do that, as also another Linux distribution use this safety policy. And it is normally to do that (UNIX behaviour), just in case of some script with bad intention (what came through internet, for example).

---

