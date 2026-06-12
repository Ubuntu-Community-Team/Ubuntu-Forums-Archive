---
title: "how find the model of my ati graphics card?"
date: 2008-07-04
forum: Hardware
---

### Post by sonaural on 2008-07-04
is it written on the hardware somewhere, i no longer have the packaging

thanks

---

### Post by SEMW on 2008-07-04
Try
```
sudo lshw | grep Radeon
```

---

### Post by starcannon on 2008-07-04
To find out what video card model you have regardless of make:

```
lshw -C display
```

---

