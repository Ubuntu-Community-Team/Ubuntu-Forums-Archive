---
title: "cpu throttling 800/1600/1800"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by crd on 2006-02-19
I've been trying to get my CPU frequency scaling working properly for some time now, and it works to some degree but not completely.

The processor is an AMD Turion ML-32 3400+ that runs at 1800MHz, 1600MHz and 800MHz, and I am using **powernowd** to handle the scaling and **cpuinfo** to watch the speeds.

If I manually set the governor to "powersave," it goes straight to 800 MHz, which is the result you'd expect.
 > *cpufreq-selector -g powersave*

Then, if I change it to "ondemand," it remains at 800 MHz until the instant I use more of the processor, such as moving a window, and it increases up to 1800MHz.
> *cpufreq-selector -g ondemand*

After I stop moving the window, it goes down to 1600MHz, but never below that.  So, it works switching dynamically between the 1600 and 1800 levels, but it never goes down to 800 unless i call the "powersave" option again.

Since it runs pretty hot at the higher frequencies, I'd ultimately like to switch between 800/1600/1800 on the fly.

Any suggestions?

---

### Post by heimo on 2006-02-19
*lol* Thank you very much for asking these questions, as that's why I noticed that my Athlon is running at 1.1GHz and not 1.9GHz as it should. :D Anyway, I'm not really expert on frequency scaling, but you could check if adding "CPU Frequency Scaling Monitor" helps you at all (I don't know if it can be used to change the clock rate, as my CPU doesn't support scaling.)

---

### Post by crd on 2006-02-21
After pawing through a number of postings, I ran across one that suggested adding:

*noapictimer irqpoll*

to your kernel boot line, and it worked in fixing my throttling issue.  CPU runs cooler, fan runs less, and battery life is up!

Beware, apparently using this setting could cause adverse effects on your system, so read up on it before trying it out.

---

