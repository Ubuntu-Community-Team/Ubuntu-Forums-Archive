---
title: "i8kfan and Inspiron 1525"
date: 2009-09-06
forum: Hardware
---

### Post by parrado on 2009-09-06
Hi,

I have an Inspiron 1525 with Ubuntu 9.04

Kernel: 2.6.30.5
CPU: Intel Core 2 DUO 2.0 GHz
RAM: 2 Gb

i have experienced some touchpad heating issues, so i installed i8kutils + gkrellm with help of "sensors panel". Additionally, my cpu freq-scaling governor is "ondemand" for both cpus and it works fine.

When i use i8kfan utility it returns

0 1.

and i8kspeed returns mostly of times

0 90000

some times second value increases when CPU temperature increases.

Problem is, i can't set-up new settings with i8kfan, i.e., i8kfan 2 2 always returns

0 1

in spite of given setting.

Why i can't change fans settings?

Why left fan is always turned off?

Can i increase temperature threshold for fans? how can i do it?

How can i reduce my laptop heating at touchpad? This is the biggest issue.

Best regards and thanks in advance.

---

### Post by emmiesix on 2009-10-01
I have the same problem on a new Inspiron 17 (1750).  Flashing the bios is not viable since there is only one version. :(

---

### Post by Onesimus on 2009-10-01
I use gkrellm all the time.  

You say that you have installed it, but are you running it.  There should be a window that comes up that you can right click on.

Select Configuration, then select Plug-ins, then Dell i8k plugin

You can modify temperatures using the Temperature Tab.  

To run gkrellm, press F12 and type gkrellm at the prompt.

---

