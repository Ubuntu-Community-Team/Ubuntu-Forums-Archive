---
title: "Make mouse toggle permanent using psmouse module"
date: 2009-06-12
forum: Hardware
---

### Post by dileepm on 2009-06-12
Hi,
I have Acer notebook whose touchpad toggle button seems to have a bug. If i switch it off then touchpad function is off when i turn on, the touchpad doesn't turn on again. Well i managed it to work by reloading the psmouse module using

```
modprobe -r psmouse
modprobe psmouse
```But all i need is how do i make this thing auto so that touchpad toggle works on its own unlike commanding manually

---

### Post by edu77pose on 2009-06-18
> **dileepm said:**
> Hi,
I have Acer notebook whose touchpad toggle button seems to have a bug. If i switch it off then touchpad function is off when i turn on, the touchpad doesn't turn on again. Well i managed it to work by reloading the psmouse module using

```
modprobe -r psmouse
modprobe psmouse
```But all i need is how do i make this thing auto so that touchpad toggle works on its own unlike commanding manually

Thanks for that, I've been wondering how to get over that hurdle (saves me from rebooting).

Any idea how to make it work on the touchpad toggle button???

That would be grande!
Cheers,

---

