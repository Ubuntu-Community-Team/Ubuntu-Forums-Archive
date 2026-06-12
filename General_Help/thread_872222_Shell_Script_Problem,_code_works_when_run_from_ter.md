---
title: "Shell Script Problem, code works when run from terminal, but not when run from script"
date: 2008-07-27
forum: General Help
---

### Post by turiya on 2008-07-27
Nevermind

---

### Post by geirha on 2008-07-27
The error is in the first line, the sh-bang.

In the terminal you are using /bin/bash, but the script is run as /bin/sh, which is dash, a less feature rich shell.

change the first line to read ```
#!/bin/bash
```

---

### Post by turiya on 2008-07-27
Forgot to mention. The random works, but it doesn't work as well as I would like it to, does anyone have any suggestion on making the random better.

---

### Post by turiya on 2008-07-27
I swear I had tried that as /bash and it didn't work, but it's working now for whatever reason

---

