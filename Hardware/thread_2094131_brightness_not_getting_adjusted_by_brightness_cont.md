---
title: "brightness not getting adjusted by brightness control keys."
date: 2012-12-12
forum: Hardware
---

### Post by sumantdev90 on 2012-12-12
I am using ubuntu 12.04 in my sony vaio VPCEH38FN E series laptop. The brightness is always set to maximum and when i try to adjust it by brightness contol keys ,no effect is there.There is no such problem when i run windows. What to do?

---

### Post by Toz on 2012-12-13
Hello and welcome to the forums.

What video card do you have and which driver are you using? Can you open a terminal window, run the following commands and post back the results:
```
sudo lspci -vnn | grep -A12 VGA
```
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
```
cat /var/log/dmesg | grep -i brightness
```

Lets see what you've got.

---

