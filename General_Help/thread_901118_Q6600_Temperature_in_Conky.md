---
title: "Q6600 Temperature in Conky"
date: 2008-08-26
forum: General Help
---

### Post by bamu07 on 2008-08-26
Hi all, i'm having a little trouble getting conky to display the temperatures for my Q6600's cores. Months ago when i did this, i think the variable was like...
${coretemp0 temp1}
but i can't get it to work now; any help would be appreciated!

---

### Post by jolx on 2008-08-26
well mine is like this:
> CPU  1: ${alignr}${hwmon 1 temp 1}  C
CPU  2: ${alignr}${hwmon 2 temp 1}  C

hwmon is used in conky to disply the outputs of lm_sensors

---

### Post by bamu07 on 2008-08-26
Doesn't work with a quad core it seems

---

### Post by jolx on 2008-08-26
im pretty sure it is compatable with quad cores, as it would be depending on which motherboard you have and whether it has hardware sensors, and also whether those sensors are supported.

And you need to install lm-sensors
```
sudo apt-get install lm-sensors
```

and then run 'sudo sensors-detect'

---

