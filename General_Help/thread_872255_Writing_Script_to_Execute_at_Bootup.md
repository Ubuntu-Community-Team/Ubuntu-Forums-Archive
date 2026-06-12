---
title: "Writing Script to Execute at Bootup"
date: 2008-07-27
forum: General Help
---

### Post by sjrlaw on 2008-07-27
Every time I boot my machine, I lose my wireless network connection.  I have to go into the terminal and do a manual config.  How would I write a script to do this and auto run at bootup?  Thanks!

---

### Post by spiderbatdad on 2008-07-27
are you using ndiswrapper? did you add it to /etc/modules?

---

### Post by iaculallad on 2008-07-27
> **sjrlaw said:**
> Every time I boot my machine, I lose my wireless network connection.  I have to go into the terminal and do a manual config.  How would I write a script to do this and auto run at bootup?  Thanks!

Are you currently using ndiswrapper?

---

### Post by sjrlaw on 2008-07-27
Nope; not using ndiswrapper.

---

### Post by Vivaldi Gloria on 2008-07-27
> **sjrlaw said:**
> Every time I boot my machine, I lose my wireless network connection.  I have to go into the terminal and do a manual config.  How would I write a script to do this and auto run at bootup?  Thanks!

Save your script somewhere and try editing the /etc/rc.local file and putting the script there as follows:

```
/path_to_script/script &
exit 0
```

---

