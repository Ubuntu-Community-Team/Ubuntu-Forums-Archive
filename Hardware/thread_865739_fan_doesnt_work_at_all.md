---
title: "fan doesnt work at all"
date: 2008-07-20
forum: Hardware
---

### Post by vanwarantion on 2008-07-20
Hello (sorry for my poor english),
first i thought i couldnt adjust cpu speed because when i was trying to do somethings like watching youtube videos or some other things that makes cpu work hard, i saw that cpu speed goes like between 600 and 300mhz. so i was thinking that i had some problems with speedstep. in my aopen ms241 barebone, there is no spesific cpu speed setting in bios (only "max performance" and "max battery"). then i noticed this situation is heat related because when laptop reduces the cpu speed it was doing that only when cpu gets hot. and by saying hot, i mean "risk of machine forced family planning on lap" hot.

i think it does that because of fire hazard or something. so i am trying to make the cpu fan work but i noticed it doesnt spin when i boot ubuntu.
there is nothing in /proc/acpi/fan/

my cpu model name is "Intel(R) Pentium(R) M processor 1.60GHz"

"# cat /proc/acpi/thermal_zone/THRC/temperature" returns
temperature:             71 C

i couldn't work with lm-sensors because sensors-detect command returns "Sorry, no sensors were detected." at the end.

i see these lines in lsmod output:
i2c_dev                 8836  0 
i2c_i801               10640  0 
i2c_core               24832  2 i2c_dev,i2c_i801

What can i do now?

---

### Post by vanwarantion on 2008-07-20
ps: cpu heat seems "temperature: 71 C" in previous message because about half  a minute ago i was sprayed almost a half tube of lighter gas trough the grill that normaly cpu fan sucks air. and it worked because temperature is usualy around 95-110 celsius.

---

