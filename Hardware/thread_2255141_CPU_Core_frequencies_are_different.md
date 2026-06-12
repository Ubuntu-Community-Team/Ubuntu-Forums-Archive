---
title: "CPU Core frequencies are different"
date: 2014-12-02
forum: Hardware
---

### Post by hodja on 2014-12-02
Hi all,

I have checked my new (to me) Core 2 Duo E7300 2.66 CPU with Hardinfo and it shows core frequencies of each core different. Core one shows 1600 Mhz,  core two 2667 Mhz. 

Should they be the same Mhz or does this mean there is a problem with the CPU? 

Thanks in advance

---

### Post by QIII on 2014-12-02
The most likely cause is that something had spawned a single thread that was consuming the resources of one of the cores.  Perhaps it was hardinfo itself.  Under load, the core in use is either partially or fully un-throttled to handle tasks.

Try looking at this when nothing else is running.  Your BIOS may even have a "PC Health" menu you can use at that stage.

---

### Post by Doug S on 2014-12-02
All cores of current and older intel processors are driven from one pll, and therefore are always at the same clock frequency. In the future there will be processors with multiple pll's (or so I recall reading somewhere) Depending on which cpu frequency governor you are using the reported CPU clock frequency might actually be what was requested and not what it is (for example acpi-cpufreq), or will be an average over per core active time during the last sample interval (for example the intel_pstate driver). There is not a problem with your CPU.

---

### Post by tgalati4 on 2014-12-02
Load up your cpu's with cpuburn.

```
sudo apt-get install htop
sudo apt-get install cpuburn
burnP6 &
burnP6 &
burnP6 &
burnP6 &

```

Open *htop* in another terminal to watch the cpu's.  Install a CPU meter on your panel so you can see the clock speed.

Kill the processes with *htop* or with:

```
sudo killall burnP6
```

---

### Post by hodja on 2014-12-03
Thanks for all the input. Will follow all the advice and post results here.

---

