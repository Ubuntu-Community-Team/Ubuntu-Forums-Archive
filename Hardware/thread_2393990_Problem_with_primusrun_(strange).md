---
title: "Problem with primusrun (strange)"
date: 2018-06-11
forum: Hardware
---

### Post by zohran on 2018-06-11
Hello, i have strange problem with primusrun command. I have installed bumblebee because i have hybrid graphic card. When i test primus with firefox, my card switch correctly to nvidia card, but when i launch primusrun with dolphin-emu, primus complain he don't found nvidia module...

```
zohran@msi-gs73vr-6rf:~$ primusrun dolphin-emu
/usr/bin/primusrun: ligne 41: avertissement : command substitution: ignored null byte in input
primus: fatal: Bumblebee daemon reported: error: [XORG] (EE) Failed to load module "nvidia" (module does not exist, 0)

zohran@msi-gs73vr-6rf:~$ primusrun firefox
/usr/bin/primusrun: ligne 41: avertissement : command substitution: ignored null byte in input
```

Any idea ?

---

