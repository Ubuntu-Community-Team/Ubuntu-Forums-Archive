---
title: "Orange PI Zero+ using Ubuntu: problem GPIO path"
date: 2018-06-28
forum: Hardware
---

### Post by py5bk on 2018-06-28
Hello friends!
I'm using on my Orange Pi Zero + board the Ubuntu system. At first it's perfect. I made the package installations perfectly.
But I'm having trouble working with the gpio pins. I used Armbian before, but I'm having trouble with the analog audio card when I use Armbian, which is not the case with Ubuntu.
My problem when using the Ubuntu image in my Orange Pi Zero + is that the gpio is different. Its path is /sys/class/gpio_sw instead of /sys/class/gpio ..
I would like to know if it is possible to change this system from gpio to the one I can work like armbian ..
I usually command the ghosts as follows:

```
 echo 14 > /sys/class/gpio/export
 echo out > /sys/class/gpio/gpio14/direction
  echo 0 > /sys/class/gpio/gpio14/value
 echo 1 > /sys/class/gpio/gpio14/value

```

Can someone help me with this?

From now on I am very grateful for the attention!

---

