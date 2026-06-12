---
title: "conky problems"
date: 2008-11-06
forum: General Help
---

### Post by rkakkar on 2008-11-06
my conky window is staying above my normal windows. how can i fix that? see screenshot for details.

---

### Post by uber_nerd11 on 2008-11-08
Are you trying to have conky start up with your computer when you log in?  If so you need to create a script to delay they start up of conky and put that script into your session start up.

For example the script I have for conky:

#!/bin/bash
sleep 10 && conky

This will cause the system to wait for ten seconds and then start conky.  From what I have read on other forums, the reason conky is staying on top of your windows is that it tried to load before your window manager has finished loading.  You need to let your window manager finish before conky starts and this delay allows that to happen.  Feel free to change the "10" to any delay in seconds you want.

---

