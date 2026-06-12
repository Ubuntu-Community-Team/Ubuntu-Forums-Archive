---
title: "Dell Laptop hot docking/undocking loses serial port"
date: 2019-03-06
forum: Hardware
---

### Post by hackerb9 on 2019-03-06
I've discovered that the [FONT=Courier New]agetty[/FONT] login process on the serial port of a Dell Latitude e7240 Ultrabook gets very confused when the laptop is docked or undocked. It repeats an error message that "/dev/ttyS0: not a tty". Even weirder, it seems to be right. Checking with the [FONT=Courier New]setserial[/FONT] command, ttyS0 doesn't even have a UART type. This is likely a bug in the Linux kernel as that should *never* happen. Fortunately, I can fix it by running,

```
sudo setserial /dev/ttyS0 autoconfig
```

However, I'd like to make it automatic. Where are the scripts that are run whenever a machine is docked/undocked?

Thanks!

---

