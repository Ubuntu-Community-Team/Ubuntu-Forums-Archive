---
title: "Terminal/installer error"
date: 2008-08-09
forum: General Help
---

### Post by halocog on 2008-08-09
Hello, i am getting an error when i go to install something either from a .DEB or in terminal, the package installer says "Only one software management tool is allowed to run at the same time" . 

i have nothing else running that could be it, i have rebooted 2 times also.

does anyone know how i can fix this?


-thanks-

---

### Post by halocog on 2008-08-10
also, when i open synaptic package manager, i get the error 

"E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"
"E:_cache->open() failed,please report."

see included screenshots.

---

### Post by Mister.Vash on 2008-08-10
Have you ran that command?

Open up a terminal and run
```
sudo dpkg --configure -a
```

It works, try synaptics again, if it doesn't, post the output

---

### Post by halocog on 2008-08-10
thank you! i was running the command without sudo in the front. 

it must have been caused by me closing a installer early.

---

