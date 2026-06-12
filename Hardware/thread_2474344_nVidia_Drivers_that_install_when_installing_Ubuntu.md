---
title: "nVidia Drivers that install when installing Ubuntu"
date: 2022-04-26
forum: Hardware
---

### Post by picklemorty282 on 2022-04-26
As you all know, when installing Ubuntu, you are treated to choosing whether you want to install third-party drivers.


When I installed Ubuntu, I chose that option. After it was done installing, I noticed something. In the "Additional Drivers" tab of software-properties-gtk, it stated that there was a manually installed driver. Therefore, it is implied that a different nVidia driver than the normal one is installed, specifically for Ubuntu.


Could anyone tell me which one is it and state the package name of this driver too?


Thanks in advance.

---

### Post by him610 on 2022-04-26
When run from a terminal, the results will show you which GFX driver is being used.
```

inxi -Gxx

```

---

