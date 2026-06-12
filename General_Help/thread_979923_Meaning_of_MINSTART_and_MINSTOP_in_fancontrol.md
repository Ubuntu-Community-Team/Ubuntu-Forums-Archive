---
title: "Meaning of MINSTART and MINSTOP in fancontrol"
date: 2008-11-12
forum: General Help
---

### Post by Cephalotus on 2008-11-12
Hi all,

I'm setting up my fancontrol configuration file using pwmconfig (lm-sensors 3.0.3) but I'm not able to understand the MINSTART and MINSTOP parameters meaning. I know that they are relative to the pwm value (from 0 to 255).
Actually pwmconfig set them automatically to MINSTART=150 and MINSTOP=0.

Please can someone explain me what these values mean?

The lm-sensors man page says:
MINSTART : Sets the minimum speed at which the fan begins spinning. You should use a safe value to be sure it works, even when the fan gets old.
MINSTOP : The minimum speed at which the fan still spins. Use a safe value here, too. 

But for me these definitions are hard to understand... :confused:

Thank you

---

