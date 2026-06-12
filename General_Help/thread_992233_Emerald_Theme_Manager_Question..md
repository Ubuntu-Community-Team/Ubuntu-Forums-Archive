---
title: "Emerald Theme Manager Question."
date: 2008-11-24
forum: General Help
---

### Post by V0los on 2008-11-24
I'm running Compiz Fusion on Intrepid Kubuntu, And in finally got Emerald to run but only when I put ```
#emerald --replace
``` 
But when I close Konsole Emerald stops running.
Is there a solution to this?

---

### Post by walkerk on 2008-11-24
Create a small script.
```
nano ~/.emerald.sh
```
```
#!/bin/bash
exec emerald --replace &
```

Make it executable.
```
chmod +x ~/.emerald.sh
```

Run it.
```
~/.emerald.sh
```

Edit: Replaced gedit w/ nano because your not using gnome.

---

### Post by V0los on 2008-11-24
Awesome, That worked. Thank you.:)

---

### Post by walkerk on 2008-11-24
> **V0los said:**
> Awesome, That worked. Thank you.:)

You're welcome :)

---

