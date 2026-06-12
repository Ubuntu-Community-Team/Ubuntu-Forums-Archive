---
title: "Fan not responding to CPU temp rise"
date: 2008-09-23
forum: Hardware
---

### Post by RobJDean185 on 2008-09-23
Basic problem - I have a Dell Precision 490 with dual Xeon processors that pump out a lot of heat. In the diagnostics, the fans speed up fine so they can run fast, but in Hardy under load, the fans never speed up.

I've installed the sensors package and coretemp module, and this showed earlier this week that while running a heavy load, a couple of the cores hit 100C with the other six not far behind. I shut everything down to cool off.

I've investigated this on several Linux distros and the results appear to be the same. I'm still trying to understand whether this is something the BIOS ought to control or if I can exert more control with appropriate drivers in Ubuntu (which is my preference).

One other note is that sensors-detect reports that the SMSC chip has ID 0x6701 and is not supported. I'm still trying to track down whether there is anything I can do about this or if I have to go back ten years and brush up on my own coding.

I've been looking at dellfand, the i8k module, and will be looking into i8kutils from the Debian distro. No success so far though. However, any early pointers or suggestions might save me time in the long run. I'll update here as I make progress (hopefully).

The worst case scenario is I have to drop back to Windows. :eek:

---

### Post by TheLions on 2008-09-23
Did you try to disable Intel SpeedStep in BIOS(if you have that)???

---

### Post by RobJDean185 on 2008-09-23
I found that dellfand was reporting a fan speed on fan 0, so figured it must be finding something. However, it was also reporting CPU temp of -1, even though lm-sensors was giving the correct temps on all available cores. Hence dellfand wasn't exerting any control.

The dellfand code includes a set_fan function based on some assembler code which takes a fan number as a parameter. Dellfand only uses Fan 0, so I hacked the code quickly to cycle through more fans until it stops getting any speed detection. On my 490 it found 3 fans. I also hacked the code to force the fans to high speed.

What I now have is a modified dellfand which is successfully forcing all three fans to high speed but isn't detecting CPU temperature. That means lm-sensors gives me the means to detect the core temps and the dellfand assembler code gives me the means to set the fan speeds.

My hacked version can keep the fans at high speed which knocks about 20C off the processors and 10C off the GPU. In practice, the airflow looks poor since four cores are running 20-30C hotter than the others (up to 85C) but that's another job.

So all the pieces are in place - just need them pulling together and some correction on airflow. Linking lm-sensors and the dellfand code might be a bit beyond my meagre coding experience, but worth a try.

Also, another thread is looking at the lack of i8k module on 64bit architecture in [http://ubuntuforums.org/showthread.php?t=517830](http://ubuntuforums.org/showthread.php?t=517830). Maybe the dellfand code is useful there?

---

