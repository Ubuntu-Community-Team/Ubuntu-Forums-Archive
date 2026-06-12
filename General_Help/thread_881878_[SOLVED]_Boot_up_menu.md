---
title: "[SOLVED] Boot up menu?"
date: 2008-08-06
forum: General Help
---

### Post by Dave Otter on 2008-08-06
Every time I boot Hardy 8.04 what I assume is the Boot up menu appears even though it is not ticked in Start up.
   Any ideas how I can remedy this?

       Many thanks

---

### Post by rEbyTer on 2008-08-06
I don't know what you really mean, but if you want to boot up without the 3sec timeout, you may go to **/boot/grub/menu.lst** and search for 'timeout' then change it to 0.

Hope this helps.

---

### Post by Dave Otter on 2008-08-06
Message asks which OS I want to use,only have 8.04 loaded!

---

### Post by jonian_g on 2008-08-06
Open a terminal and type:

```
sudo apt-get install startupmanager
```

Then go to System>Admin>Start-up manager. Check "Use timeout in....." and set "timeout in seconds" to zero. This way you wont get a list when system starts.

---

### Post by Dave Otter on 2008-08-07
Thanks to all who responded

---

