---
title: "[SOLVED] Since Hardy, no laptop mode when on AC power"
date: 2008-05-05
forum: Hardware
---

### Post by vussvillem on 2008-05-05
In Gutsy Gibbon I was able to make laptop mode active when on AC power. In Hardy Heron, configuring "/etc/laptop-mode/laptop-mode.conf" file to "ENABLE_LAPTOP_MODE_ON_AC=1" does not have any effect. Laptop mode tools are working when on battery power, but I want to have them working when on AC power as well - because of the great heat reduction on Dell D600.

I've tried to resolve the problem by downloading the latest Debian laptop-mode-tools package, it didn't help.

---

### Post by vussvillem on 2008-05-05
I am newbie so I do not understand why, but the only way I can enable laptop mode when on AC power is to execute, every time when I restart my computer, a following command: "sudo /etc/init.d/laptop-mode reload". Maybe I have to change something in that file or I have to make "sudo /etc/init.d/laptop-mode reload" to be executed every time I restart....

Please help me, the reason why I got into Linux world first place was that with the help of laptop-mode-tools I could conveniently cool down my Dell D600, model that has a well known heat issue.

---

### Post by syga on 2008-07-12
I also have this exact same problem. 

Any suggestions on how to fix this?

---

### Post by midtown on 2008-07-21
You guys may want to check out [https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement), and the related bugs it lists. There is one specifically for laptop mode in AC power. Also you may want to comment in the bugs why you find them important, and subscribe, so that they get more/proper attention.

---

### Post by vussvillem on 2008-09-23
Thanks for the reply, midtown. Your pointed wiki page solved the problem.

---

