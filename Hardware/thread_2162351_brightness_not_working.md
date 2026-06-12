---
title: "brightness not working"
date: 2013-07-14
forum: Hardware
---

### Post by yichentohjoel on 2013-07-14
i have an acer laptop with ubuntu 13.04 everything works except that the brightness control on my keyboard does not work. even adjusting it manually with the brightless and lock programme does not do anything help?

---

### Post by Toz on 2013-07-14
What model of acer notebook do you have?

Can you open a terminal window, type in the following commands and post back the results?

1. Your current kernel boot line (to see if you are using any special boot parameters):
```
cat /proc/cmdline
```

2. Information about your video card(s) and drivers:
```
sudo lspci -vnn | grep -A12 VGA
```

3. Information about your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

4. Your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

