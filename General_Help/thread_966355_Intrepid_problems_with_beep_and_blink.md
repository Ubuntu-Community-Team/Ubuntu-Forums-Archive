---
title: "Intrepid: problems with beep and blink"
date: 2008-11-01
forum: General Help
---

### Post by stinkinrich88 on 2008-11-01
Hello,

I've clean-installed intrepid yesterday. I've installed beep and blink. When I try to execute beep it says:

```
bash: /usr/bin/beep: Permission denied
```

that sucks! I never had to be root before! Can I change this?

Also, blink does not work at all. It executes with no error messages, but nothing starts blinking! Also, my scroll lock led no longer turns on even when I press scrlk. Really weird.

Any ideas?

Thanks!

---

### Post by stinkinrich88 on 2008-11-07
solve the beep issue by opening a root file manager (gksu nautilus) then finding /usr/bin/beep and enabling "allow executing of file as program" on permissions tab of properties.

Still no joy with blink at all! I really, really want it!

---

