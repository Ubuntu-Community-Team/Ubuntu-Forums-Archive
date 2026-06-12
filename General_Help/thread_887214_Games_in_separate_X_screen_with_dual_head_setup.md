---
title: "Games in separate X screen with dual head setup"
date: 2008-08-11
forum: General Help
---

### Post by maddog39 on 2008-08-11
Hey everyone,

I have a dual head setup to use separate X screen (primary: CRT, secondary: HDTV). The only problem is that apparently that separate X screen doesnt exist according to glxinfo:
```

$ glxinfo | grep screen
display: :0  screen: 0

```Even though the nvidia-settings dialog sees both monitors and both monitors work as expected. So how come its not showing up?

Thanks!
-Alec

---

