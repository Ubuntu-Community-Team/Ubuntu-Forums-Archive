---
title: "Fan speed at max after suspend"
date: 2016-10-07
forum: Hardware
---

### Post by enverhoxha on 2016-10-07
In System Monitor (ksysguard) there are 5 temperature sensors (acpitz-virtual-0). If I suspend for a longer time ( the system cools down completely) and then resume, the 3rd sensor instantly displays 75 degrees and climbs quickly to 100 degrees C and stays there, while the fan speeds up at max. But the CPU is cold! 
The only way to get the fan back to normal is to suspend again and then resume immediately. The 3rd sensor temperature drops from 75 degrees to 0 (!) and then climbs to a decent value - usually close to the CPU's.
Now if I suspend again after a couple of minutes and resume immediately, sometimes the sensor rockets once more (and the fan speed), sometimes it goes down. The initial temperature seems to be always 75 degrees!
It's very annoying. What can I do to correct this behavior? (This doesn't ever happen at boot.)

---

### Post by P_Aleksandrov on 2016-10-09
What hardware and Kubuntu and kernel versions do you use? Could you show the output of "sensors -u" command?

---

