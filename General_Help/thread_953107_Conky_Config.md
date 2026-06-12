---
title: "Conky Config?"
date: 2008-10-19
forum: General Help
---

### Post by mzh4ng17 on 2008-10-19
Conky works really well whenever I start it from Terminal. However, when I tell Sessions to start conky on startup, it starts up in the foreground, so any windows I open are hidden behind my conky scripts. Does anyone know why this happens or how to fix it?

---

### Post by easybake on 2008-10-19
You just need to add a sleep script to it. It is just drawing the window out of order.

in terminal type```
gedit .startconky
```
paste this```
#!/bin/bash

sleep 20 &&
conky
```
save and close
in terminal type```
sudo chmod +x ./startconky
```

Remove any instance of conky from your sessions. Add a new sessions entry with the command ```
./startconky
```

You're done.

mark this thread as solved when you're done.

---

