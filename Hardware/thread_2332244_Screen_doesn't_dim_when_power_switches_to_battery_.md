---
title: "Screen doesn't dim when power switches to battery in Ubuntu 16.04"
date: 2016-07-29
forum: Hardware
---

### Post by Daniyal_Javani on 2016-07-29
Hello, I try following script form [https://ubuntuforums.org/showthread.php?t=2165826&p=12780831#post12780831](https://ubuntuforums.org/showthread.php?t=2165826&p=12780831#post12780831)
```
#!/bin/bash
case $1 in
    true) #on battery
        echo XX > /sys/class/backlight/INTERFACE/brightness
        ;;
    false) #on ac
        echo YY > /sys/class/backlight/INTERFACE/brightness
        ;;
esac
```
but still nothing happen when power unplugged. Also try different brightness for different states. Can you please help to solve this issue.

---

