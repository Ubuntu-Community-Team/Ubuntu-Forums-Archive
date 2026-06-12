---
title: "Switch on webcam LEDs ?"
date: 2010-11-27
forum: Hardware
---

### Post by dargaud on 2010-11-27
Hello all,
for a project of mine I'd like to be able to control the 4 LEDs present on a Hercules webcam (driver sonixj). The webcam works fine, but I don't know how to control the LEDs. I ran some searches and aparently no Linux app uses camera LEDs, they only care about the video flux. There were some pointers to /sys/class/leds but I don't have that. Also some talks about using GPIOs, which I know how to use on embedded devices, but here I don't know which one it could be: ```
$ find /sys/ -iname "*gpio*"
/sys/bus/platform/drivers/tc35892-gpio
/sys/bus/platform/drivers/timb-gpio
/sys/bus/platform/drivers/ucb1400_gpio
/sys/bus/platform/drivers/mdio-gpio
/sys/bus/pci/drivers/langwell_gpio
/sys/class/gpio
/sys/kernel/debug/gpio

```
Any pointers ? Thanks.

---

