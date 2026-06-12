---
title: "Cpu Frequency Scaling i5 540m Mobile Processor ??"
date: 2010-11-23
forum: Hardware
---

### Post by excetara2 on 2010-11-23
I used to run the same system I have now but the only change was it was running a core 2 duo which I used cpufreqd to control the frequency scaling. I know the i5 has a turbo mode that I was wondering was built into the linux Kernal yet or plans too. If not, can cpufreqd be used to control the frequency of the i5 because I can't seem to get it working.

Is frequency controlling necessary on the i5 or best to leave it on onDemand??

Lastly, is there a command to set the cores in performance mode if turbo boost doesn't work?? Sometimes I would like to do this and then switch back to ondemand when I'm done doing settings that require the frequency high for an extended period.

---

### Post by admiralspark on 2010-11-23
Well, I'll answer the second part first because it's the easiest.
Right click on your top bar, click 'Add to Panel', then click on the 'CPU Frequency Scaling Tool'. Then, simply click on the new button it adds to change your CPU clock and behavior. If you want to save power, use powersaving. If it's under normal use, use on-demand. If you're gaming/rendering, use performance (ondemand will stutter as it adjusts clocks).

For the first question....as of Linux kernel 2.6.33, Turbo Boost is supported and according to [here]("http://ubuntuforums.org/showpost.php?p=9168574&postcount=10") it works fine. However, from what I'm reading, the ACPI (especially in laptops) can disable or not activate the feature....you can be sure to get it by booting with 'acpi=off', but then you have absolutely no power management. So, not recommended.

I'd test it with something like blender that would use up alot of CPU/GPU power. My i7 shows it working, but it won't come under use unless you completely max out the CPU.

EDIT: 10.10 kernel is 2.6.35 unless I'm mistaken. So it has support.

---

### Post by excetara2 on 2010-11-23
Using the frequency scaling thing is annoying because have to set each kernel independently. Also think there is a problem because cpufreq-info states that processor 0 has to be 1.20Ghz. The other three threads can fluctuate but this doesn't seem to be right.

acpi off is unfortunately not an option but I'd read heaps and can't seem to get to the bottom of it.

How did you see it working?? did you use the i7z app or what did you use??

I use Lucid with 2.6.36. Maybe I should grab 2.6.35 because 2.6.36 is just a proposed update and see how it goes.

Cheers

---

### Post by excetara2 on 2010-11-23
Also, how do you check what is currently controlling the frequency scaling?? Like what program?

---

