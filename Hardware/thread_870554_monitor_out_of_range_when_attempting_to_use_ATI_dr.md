---
title: "monitor out of range when attempting to use ATI driver"
date: 2008-07-25
forum: Hardware
---

### Post by silencer07 on 2008-07-25
i have ATI 9550 se in my agp slot. my pc is 5 years old. my driver in windows is working fine but when i attempt to use the driver using hardware driver manager my monitor says that it is "out of range". i tried to adjusting my resolution in 1024 * 768 with 60hz refresh rates but the problem persists. currently i am not using the driver which slows down any graphic intensive applications e.g celestia. 

Any help from you guys will be appreciated. Thank You

note: my "vista" monitor is ancient :)

---

### Post by markbuntu on 2008-07-26
Try running this command in a terminal. it will reconfigure your x server:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by silencer07 on 2008-07-29
i tried it via recovery mode. but when i resumed the normal login, ubuntu is not using anymore the restricted drivers. what shall i do? how can i set that the monitors maximum resolution is only 1024 by 768 with refresh rate of 30-56khz for horizontal and 50-85hz for vertical

---

