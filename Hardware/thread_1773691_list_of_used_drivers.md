---
title: "list of used drivers"
date: 2011-06-02
forum: Hardware
---

### Post by roshats on 2011-06-02
I have desktop with Ubuntu 9.10 . Now i want to install something new ( maybe Lubuntu 11.04 ). At desktop i use dlink dwa 110 to give wireless access to laptop. Does lubuntu has drivers for dlink dwa 110? when i load lubuntu in LiveCD mode i can't create wireless network. How can i get list of all drivers currently using by ubuntu 9.10 to select drivers for dlink and then install it in lubuntu?

---

### Post by Yellow Pasque on 2011-06-02
lsmod - see all kernel modules loaded
sudo lshw - shows what driver each device uses

---

### Post by roshats on 2011-06-06
Thanks, this is what I was looking for.

---

