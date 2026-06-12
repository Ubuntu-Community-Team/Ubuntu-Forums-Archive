---
title: "Suspend/Sound I have the fix and want to automate it!"
date: 2008-10-31
forum: General Help
---

### Post by bcn17 on 2008-10-31
I am using 8.10- After suspend sound does not work until I type into terminal:
```
sudo /etc/init.d/alsa-utils restart
``` 
How can I automate this when coming out of suspend? Thanks!

---

### Post by dcstar on 2008-10-31
> **bcn17 said:**
> I am using 8.10- After suspend sound does not work until I type into terminal:
```
sudo /etc/init.d/alsa-utils restart
``` 
How can I automate this when coming out of suspend? Thanks!

There are scripts that are run going into/out of hibernate etc. that you can modify, I cannot remember them but a forum search should provide the answer.

---

