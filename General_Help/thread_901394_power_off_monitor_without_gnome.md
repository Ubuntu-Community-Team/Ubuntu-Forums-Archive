---
title: "power off monitor without gnome"
date: 2008-08-26
forum: General Help
---

### Post by sarvirtual on 2008-08-26
I recently installed a ubuntu 8.04 server on my pc. I noted that if i didn't use gnome but only console command my monitor after è delay time goes in power off . I didn't find a solution without installing gnome.
Is it possible to set my configuration in order to have no power off without gnome?
Thanks for help.

---

### Post by raphaelr on 2008-08-27
You want to power off your monitor from Terminal? ```
sleep 1 && xset dpms force off
```The sleep 1 is pretty important so don't leave it out.

---

### Post by sarvirtual on 2008-08-28
Thanks for your support, but i didn't very well your suggestion
referred to your question. I need to bypass the power off after about 30 minutes. I need to have monitor live ever.
Your command realizes that?????
Again thanks
Emilio:confused:

---

### Post by raphaelr on 2008-08-29
Then its xset dpms force on.

---

### Post by sarvirtual on 2008-08-29
Very Very Thanks
:guitar:

---

