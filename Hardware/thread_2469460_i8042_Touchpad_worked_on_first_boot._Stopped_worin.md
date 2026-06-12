---
title: "i8042 Touchpad worked on first boot. Stopped woring after updates"
date: 2021-11-30
forum: Hardware
---

### Post by bleack on 2021-11-30
Hello,
my issue is the touchpad worked before software updates. After restarting it's no longer detected. That's very unusual from a user point of view

I figured out I can fix it with ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
```

but the issue is that I worked before and then it suddenly stopped. I've tried several distros in the past few days and ubuntu is the only one where the touchpad worked initially so I was very happy with it. It's unfortunate that it stopped working

---

