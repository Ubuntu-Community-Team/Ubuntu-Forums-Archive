---
title: "[SOLVED] Startup script problems.. Need a little help"
date: 2008-11-05
forum: General Help
---

### Post by slinkey1981 on 2008-11-05
Ok, I am trying to run Conky, Tilda, and ushare from one script as they  need the same amount of "sleep" so as not to be shadowed by Compiz. Well, ushare doesn't, but anyways.....

I have NEVER written a script before, but this is what I am trying.

```
#!/bin/bash
sleep 15 && conky;
& tilda -h; 

```

Conky comes up, but tilda never does start unless I alt-f2 start it, or from a terminal...

---

### Post by kerry_s on 2008-11-05
it doesn't need to be complicated, just put it straight down:

#!/bin/sh

sleep 15
conky
tilda -h

---

