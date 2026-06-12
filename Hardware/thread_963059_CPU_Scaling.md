---
title: "CPU Scaling"
date: 2008-10-29
forum: Hardware
---

### Post by rogirwin on 2008-10-29
I have a HP 6710b Laptop that will run at 2.4Ghz full speed and is set to scale to 1.2Ghz or 800Mhz. It's all working fine and as it should.

Can I change the frequency that it scales to and where is it set? Are these values hardwired into the CPU or are they set somewhere by Linux? The reason I want to is to drop the 800Mhz down to lower my CPU Temperature and to conserve power.

# echo 7 > /proc/acpi/processor/CPU0/throttling will generally result in my computer becoming unstable and freezing.

$ cat /proc/acpi/processor/CPU0/throttling 
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  88%
    T2:                  75%
    T3:                  63%
    T4:                  50%
    T5:                  38%
    T6:                  25%
    T7:                  13%

---

### Post by sdennie on 2008-10-29
Depending on how you use the machine, pegging the CPU to minimum frequency may not decrease power consumption (but will certain make the machine more sluggish).  If you want to try it out, try:

```

sudo cpufreq-selector -g powersave

```

That will peg the CPU to 800Mhz.  To bring it back to scaling use:

```

sudo cpufreq-selector -g ondemand

```

You'll want to use "powertop" and "acpi -t" to see if these changes have any effect on your power consumption or heat (they probably won't if you use the machine for web/mail/chat/office type things).

You may also want to have a look at some of the links in my signature.  Many are laptop power related and, even the ones that don't directly pertain to your machine may give you ideas on how power savings is done on linux.

---

### Post by rogirwin on 2008-10-30
$ sudo cpufreq-selector -f xxx000

Will only scale it down to 800MHz or 1.2GHz and any other value will be rounded to the closest or full speed.

Are these values set by Linux/Ubuntu or the hardware? I haven't been able to find any documention on where to change them.

---

