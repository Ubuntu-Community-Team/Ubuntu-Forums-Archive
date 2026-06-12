---
title: "migrating hal mouse settings to udev ?"
date: 2010-07-13
forum: Hardware
---

### Post by suzenon on 2010-07-13
Hello.

Since 10.04 doesn't seem to use hal anymore i've encouraged a problem with my mouse. [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input) doesn't say much about mouse and i very badly need ConstantDeceleration option from my hal config. I've added .fdi policy of my DeathAdder mouse as attachment.

Can someone guide my how to move settings into udev? Maybe post his udev mouse config as example?

Will it be possible and easy done to "activate" hal in 10.04 if udev will fail?

---

### Post by suzenon on 2010-07-14
bump  xinput shows constatndecelration with value 1, no clue how to change it in udev :(


seems adding this to startup script will do the job:
xinput --set-prop "Razer DeathAdder" "Device Accel Constant Deceleration" 2

---

