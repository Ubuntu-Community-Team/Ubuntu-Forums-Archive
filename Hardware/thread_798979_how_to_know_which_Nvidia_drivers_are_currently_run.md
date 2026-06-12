---
title: "how to know which Nvidia drivers are currently running in my system?"
date: 2008-05-18
forum: Hardware
---

### Post by vblanche on 2008-05-18
Hello,

First, I'm beginner, here in the world of Linux.

second, I would like to install latest nvidia GPU drivers, I know Envy works fine. so, I might do it the "Envy" way.

but, how do you check which version of the drivers are currently installed?

thanks
vince

---

### Post by teaker1s on 2008-05-18
try this in terminal
```
gksudo displayconfig-gtk
```

---

### Post by sdennie on 2008-05-18
If you have the nvidia drivers installed, the following should work:

```

nvidia-settings -q NvidiaDriverVersion

```

---

