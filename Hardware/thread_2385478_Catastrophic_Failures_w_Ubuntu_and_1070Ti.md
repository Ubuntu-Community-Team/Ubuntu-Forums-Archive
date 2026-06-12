---
title: "Catastrophic Failures w/ Ubuntu and 1070Ti"
date: 2018-02-20
forum: Hardware
---

### Post by ggobieski on 2018-02-20
Hi all,

I recently got a new rig for deep learning, which has the following specs:
2 1070Ti
7800X Intel CPU
MSI X299 Motherboard
16gb of RAM
Corsair Bronze 750W Power supply

I installed Ubuntu on the rig as well as the CUDA Toolkit 9.0 and the latest Nvidia driver 390.25. During stressing/benchmarking the rig, I encountered problems. Midway through a stress test where I am maxing out GPU and CPU load, the system crashes. This crash can either be a hard crash or a soft crash. There doesn't seem to be anything in dmesg, kern.log, or syslog. Here are the ways I tried to fix it.
1. Maybe it was a power issue? Well, I know the rig has been tested using windows and the same setup without fault. Second, I can recreate the crash when running only a single GPU, which should pull well under 750W. I know there might be spikes, but I can't imagine 750W to be too little to support a single GPU.
2. I tried downgrading my drivers, but the results were the same.
3. I tried regular 16.04 LTS Ubuntu, 17.10 Ubuntu, and 16.04 Ubuntu with an updated kernel. None of these changed the results.
4. I tried to induce the crash by stressing just the GPUs and just the CPUs. In each case, I could not get the rig to crash.
5. I tried a different distribution of Linux, Fedora, and the rig still crashed. The driver is the same as the one I installed with Ubuntu.

Some things I think it could be: maybe the power supply, a problem with the PCI drivers, a problem with the Linux kernel (I am tried 4.09 - 4.13), or  maybe a problem with the Nvidia drivers.

Any help would be greatly appreciated.

---

### Post by ajgreeny on 2018-02-21
Your situation may be totally different to this one but the nvidia card seems to be the same, so have a read through the thread, particularly post #5.
[https://ubuntuforums.org/showthread.php?t=2385407&p=13741596&viewfull=1#post13741596](https://ubuntuforums.org/showthread.php?t=2385407&p=13741596&viewfull=1#post13741596)

Good luck!

---

### Post by ggobieski on 2018-02-21
Unfortunately that post refers to a 1070, not a 1070Ti and that driver is not available for the 1070Ti.

---

### Post by ajgreeny on 2018-02-21
Ah! Sorry about that.
I've never used an nvidia card and did not notice the Ti in your version.

---

### Post by Yellow Pasque on 2018-02-21
Are you monitoring temps in these stress tests?

---

### Post by Autodave on 2018-02-22
Monitor temps for sure. However, you said that with one GPU you had spikes? If so, that is not good: there should be no spikes at all.  What all is this power supply powering?

One card can peak at 230 watts: that is huge. 2 cards = 2 x 230 or 460 watts. Add to that anything else that is being powered and you could be beyond the limit of that power supply.

---

### Post by Autodave on 2018-02-22
More research:

Max 12V power of that PSU is 744 watts. Again, without knowing what else is using the power, you may be getting close to running out of power.

One last thought: you are doing a stress test. The likely hood of you actually running that rig at that level of performance would be rare. At least in my thought process.

---

### Post by Autodave on 2018-02-22
More info:

From what I have founfd, that MB can draw from 210 to 250 watts. So, MB and 2 GPUs maxed out would be a consumption of 710 watts. Again, you need to factor in what else that PSU is powering, but you are still getting pretty close to the max.

---

### Post by rbmorse on 2018-02-22
Other power related possibilities include under spec'd voltage regulators on the motherboard that can't handle the load and power traces to the slots that are too small.   

I haven't seen this with video cards, but I used to encounter this all the time with regard to memory back in the old days.

---

