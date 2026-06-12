---
title: "Dell Vostros 1400 fan running all the time with 12.04"
date: 2012-12-29
forum: Hardware
---

### Post by JosefF70 on 2012-12-29
Hello all,

i have a dell vostro 1400 with 12.04 recently loaded. The cooling fan is always running. i did down load the lates nividia proprietary driver but it still seems to run at 37.5 C but the fans did not run all the time with the old windows installed on it. 

Thanks Joe

---

### Post by TOMBSTONEV2 on 2012-12-30
Well how fast is it running? I know my fan on my hp mini 110-3700 is constantly running, sometimes it is just running slow enough you cannot hear it. I would hate it if I owned a laptop in which the fan didn't run constantly.

Note: Many bios manufacturers have a setting "fan always on" check your bios and set it to disabled if the option is there.

Which brings me to my next question, did you update your bios firmware recently? If so it probably enabled the previous setting. I understand windows didn't run the fan all the time, but the fact is most operating systems do not have control over the hardware fans unless you specifically tell them to control it. The fans are temp sensor and bios job.

Bringing me to my last point If the fan is controlled by a separate thermal sensor on the fan itself, that may be failing. A fan mounted thermal sensor looks like a glob on wires by the fan blades. Sometimes those fail and bingo the fan constantly spins very fast. The processor thermal sensor seems to be fine as you reported it was at 37.5c

For a more comprehensive look at what the temperatures are at in your pc install Psensor

```
sudo apt-get install psensor
```

---

