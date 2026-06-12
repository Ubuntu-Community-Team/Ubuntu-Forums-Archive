---
title: "Issues with Dell XPS L702X"
date: 2012-03-03
forum: Hardware
---

### Post by Auria on 2012-03-03
Hi,

I installed Xubuntu 11.10 (64-bits) on my Dell XPS L702X, and most things worked out of the box (nice!).

However, I need to pass  "acpi=off" to make it boot. perhaps as a consequence of this, I am not sure, the CPU frequency will not scale and is stuck at 2.2 GHz. As a consequence of this, the CPU heats more than it needs and I am stuck with very noisy fans.

The CPU is a i7-2670QM.

The XFCE frequency indicator mentions that frequency scaling is not available on my CPU (in the same line of though, cpufreqd reports failure if trying to use it).

When booting windows, the frequency scaling works as expected so I know it's supported and not disabled in the BIOS.
Any clues as to how I may proceed to keep a cool CPU and less fan noise? Thanks

---

### Post by Sonsum on 2012-03-04
The Intel i-series processors have had a nasty power problem in recent kernels. (I have an i5 and I had the same issues).

Once Precise comes out, the patch from Intel to fix the problem will be turned on by default. But if you can't wait, here's what I've done to knock about 15 degrees C off of my idle temperature.

1) install "jupiter". Jupiter is a power management app. Some people claim it reduces their power consumption (the latest linux kernels have all had pretty bad power issues) and it seems to have helped with me.

2) install a newer version of the kernel. I installed the latest precise kernel from the time (3.2.8) as opposed to the default kernel (which I believe was 3)

I'm not sure which of the two are providing the most savings, but an installation of both decreased my fresh install idle temperature from about 55 degrees C to 30-37 degrees C.

---

### Post by Auria on 2012-03-04
> **Sonsum said:**
> The Intel i-series processors have had a nasty power problem in recent kernels. (I have an i5 and I had the same issues).

Once Precise comes out, the patch from Intel to fix the problem will be turned on by default. But if you can't wait, here's what I've done to knock about 15 degrees C off of my idle temperature.

1) install "jupiter". Jupiter is a power management app. Some people claim it reduces their power consumption (the latest linux kernels have all had pretty bad power issues) and it seems to have helped with me.

2) install a newer version of the kernel. I installed the latest precise kernel from the time (3.2.8) as opposed to the default kernel (which I believe was 3)

I'm not sure which of the two are providing the most savings, but an installation of both decreased my fresh install idle temperature from about 55 degrees C to 30-37 degrees C.

Thanks for the answer!
Unfortunately Jupiter seems also unable to change the CPU frequency so it didn't make any difference. Now I wonder, from where did you install the kernel or did you build it from source? If it's relatively safe to update the kernel I will do it, otherwise maybe I will wait for 12.04, not sure :)

---

### Post by Sonsum on 2012-03-04
The kernels I get are from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

All you have to do is install the linux-image and linux-header files. I recommend installing GDebi to let you know if you are missing any .deb files when installing.

---

### Post by Auria on 2012-03-04
Ah I installed the kernel and it's a step in the right direction, definitely :) I no more need acpi=off, awesome!! :D

Now the temperature isn't that lower unfortunately; I went from 54-58 degrees to around 42-55 degrees. For some reason in the CPU frequency applet I can only set the first core to "ondemand", the other cores stick to "performance"

And checking other guides it looks like I need to write to /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor ... but such a file does not exist and I get "access denied" trying to write there even as root, hmmmm :confused:

---

### Post by Auria on 2012-03-04
Ah, this command lets me set it :

```

echo "conservative" | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```

Now down to 42-48 degrees, it's starting to get quite reasonable :) thanks for leading me in the right direction

---

