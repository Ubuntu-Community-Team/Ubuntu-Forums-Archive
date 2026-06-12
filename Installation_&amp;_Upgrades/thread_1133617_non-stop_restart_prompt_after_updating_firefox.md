---
title: "non-stop restart prompt after updating firefox"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by boddhisatva on 2009-04-23
I've run the standard system update in Ubuntu, including some updates to firefox. After the update Firefox prompts me to restart: "Your browser have been updated and needs to be restarted" each time, although I've restarted it many times, it also continues after system reboot. Any help?

---

### Post by sahabcse on 2009-04-23
hi

#ps -ax grep | firefox

#sudo killall -9 firefox

---

### Post by boddhisatva on 2009-04-23
Thanks!
It seems this funny behaviour has stopped on its own
But I'll save your code just in case :)

---

