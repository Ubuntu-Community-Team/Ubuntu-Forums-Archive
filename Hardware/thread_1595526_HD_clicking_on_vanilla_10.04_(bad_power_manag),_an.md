---
title: "HD clicking on vanilla 10.04 (bad power manag), any way to run command if on battery?"
date: 2010-10-13
forum: Hardware
---

### Post by Wilz on 2010-10-13
Hello there.

I have Ubuntu 10.04 installed on a laptop, and every time it's unplugged, the hd keeps clicking every 2 seconds, i've figured out that the problem is the power management, which is set to "128" on battery. I can get these numbers by running the command:

```
sudo hdparm -I /dev/sda | grep "Advanced power management level"
```What is changing this setting? Is it the OS or is the hardware itself?

If it's the OS, where can I change the power management settings' numbers?

If it's the hardware, how can i run a command (in this case hdparm -B254 /my/hdd) every time the laptop is unplugged, and boot / wakeup on battery?

Thank you very much.

PS: i can just run the command manually every time, but i'm looking for an automatic salution.

---

