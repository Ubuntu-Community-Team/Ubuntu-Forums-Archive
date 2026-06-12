---
title: "[SOLVED] gdm fails to load + usplash problem"
date: 2008-09-09
forum: General Help
---

### Post by spadewarrior on 2008-09-09
Hello.

I'm using xubuntu and decided to try out slim instead of gdm. Unfortunately I could not get my normal 1024x768 resolution using it and reinstalled gdm. Something went wrong and now I cannot log in with the gui until I log in to tty1 and then do a 'sudo gdm'.

I get this error: 'usplash : no usable theme found for 1024x768"
and
"screen init failed"

I cannot work out what config to change and what to change it to. I tried reinstalling the nvidia drivers but it did not help.

Any ideas?

Thanks for reading.

---

### Post by spadewarrior on 2008-09-09
I've solved it, in case anyone else has a similar problem.

This command fixed it:

```
sudo dpkg-reconfigure gdm
```

---

