---
title: "Core2 Duo CPU voltage"
date: 2010-01-01
forum: Hardware
---

### Post by lovinglinux on 2010-01-01
I have noticed that the CPU voltage is a little bit low. I know this processor family has lower CPU voltage requirements, but is it normal to have only 1.07 volts in the core?

I recently upgraded from a P4, which ran with 1.45 volts. Additionally, we had a power disturbance in the power lines this week, with the voltage being dropped to half phase. I don't know if this affected my CPU, but immediately after the power anomaly and just before I power off the machine, the CPU voltage was 1.27 volts.

Other voltage values are normal.

I'm not sure if the power is coming slightly week again, if my processor has been damaged or if this is absolutely normal.

Any thoughts?

---

### Post by prshah on 2010-01-01
> **lovinglinux said:**
>  is it normal to have only 1.07 volts in the core?

we had a power disturbance in the power lines this week, 

Core2 Duo processors operate at a range of voltages from 0.85v-1.5v (I think), with lower frequencies consuming lower power.

Maybe you should start a CPU intensive job (Super PI benchmark, for example) and then check the voltage reading?

No matter what power you get from the mains, the SMPS (power supply)'s job is to ensure a steady voltage. So I don't believe that to be a factor at all.

---

### Post by lovinglinux on 2010-01-01
> **prshah said:**
> Maybe you should start a CPU intensive job (Super PI benchmark, for example) and then check the voltage reading?

I did a test with a CPU intensive application and the voltage didn't change. Nevertheless, only one core was maxed out during the test.

> **prshah said:**
> No matter what power you get from the mains, the SMPS (power supply)'s job is to ensure a steady voltage. So I don't believe that to be a factor at all.

The voltage is steady. Could it be a PSU problem?

---

### Post by lovinglinux on 2010-01-01
I'm checking the voltages with gkrellm and just noticed that the voltage of 1.07v is for the first core and the second core is 1.82v. Nevertheless, I don' know if I should trust these values. For instance, the +5V and +3V is showing 6.85 while in bios the values are in the correct range. The voltage of the first core is matching the value from the bios, but there isn't a second core voltage there. Additionally, CPU temperature is normal, around 29º C.

---

### Post by mr clark25 on 2010-01-01
if temps are normal, i would guess that its a false reading. i would think that 1.82v would make temps rise a lot.

you might get prime95 for windows and run it with wine. watch your temps, and see if it reports any errors. i would recommend running it for 24 hours, just to be safe.

if it doesnt give any errors, i would think that that is a false reading.

---

### Post by lovinglinux on 2010-01-04
I think I figured it out. I guess the vcore2 voltage is in fact the DDR 1.8v. This is what I get on the BIOS setup and the value is exactly the same as vcore2.

---

### Post by cascade9 on 2010-01-05
> **lovinglinux said:**
> I have noticed that the CPU voltage is a little bit low. I know this processor family has lower CPU voltage requirements, but is it normal to have only 1.07 volts in the core?

Sounds fine to me. 

If you arent getting any unstablity problems, then you havent got an issue IMO.

---

