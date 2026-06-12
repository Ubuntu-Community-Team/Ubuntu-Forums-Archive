---
title: "Dell Fans on Hardy only work if grellm is running"
date: 2008-05-09
forum: Hardware
---

### Post by snivek on 2008-05-09
I noticed after running Hardy for a few days that my Dell Latitude 620 was getting pretty hot and that my fans didn't seem to be working.  I searched and found a forum post that talked about installing gkrellm and i8k (module for dell fan hardware?).  Anyway, If I start gkrellm and enable the i8k module I have the ability to monitor my fans and they actually start running when the CPU gets hot.  The downside is this only occurs when gkrellm (user land app) is running and something like your fans should be controlled by the system (IMO).  Does anyone know how to get Hardy to use my fans without having to be running gkrellm?  Thanks!

---

### Post by snivek on 2008-05-09
Here is a link to the process I used to get Gkrellm to run my fans.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_monitor_CPU.2C_GPU_temperatures.2C_fan_speeds_and_voltages_.28GKrellM.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_monitor_CPU.2C_GPU_temperatures.2C_fan_speeds_and_voltages_.28GKrellM.29)

---

