---
title: "Ubuntu 19.04 support for Lenovo Yoga X390: missing autorotation"
date: 2019-08-21
forum: Hardware
---

### Post by pczekalski on 2019-08-21
I've recently switched from Lenovo Thinkpad Yoga S1 to Lenovo Yoga X390.
In S1 autorotation feature was working out of box but it does not work at all in X390.
How to handle this issue?

Thanks in advance for any help,

P.

---

### Post by pczekalski on 2019-08-21
Some updates: iio devices are present and proxy seems to work however monitor-sensors does not always show rotation (seems to be very laggy).
Works well in GDM login screen but does not at all in Gnome desktop.

---

### Post by pczekalski on 2019-09-01
> **pczekalski said:**
> Some updates: iio devices are present and proxy seems to work however monitor-sensors does not always show rotation (seems to be very laggy).
Works well in GDM login screen but does not at all in Gnome desktop.

After installing iio-sensor-proxy service works like charm. Interrestingly19.04 didn't install it by default.

---

