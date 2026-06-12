---
title: "What's this metal blob that sits on top of Pentium chip and how do I remove it?"
date: 2015-01-10
forum: Hardware
---

### Post by triciasurfer on 2015-01-10
What's this metal blob? And how can I remove this metal blob that sits between the CPU processor and a fan? I see some Philips screws, but neither regular screwdrivers nor offset ones can help.[ATTACH=CONFIG]259158[/ATTACH][ATTACH=CONFIG]259159[/ATTACH][ATTACH=CONFIG]259160[/ATTACH]

---

### Post by QIII on 2015-01-10
That "metal blob" is the heat sink the fan blows over.  The heatsink draws the heat off the CPU, transfers the heat to the air and the fan blows the hot air away to replace it with cool air.  It's part of what keeps your CPU cool.

Why do you want to remove it?

---

### Post by triciasurfer on 2015-01-10
> **QIII said:**
> Why do you want to remove it?

QIII, thank you for your reply. I'd like to remove it so that I could see what chip model is underneath and upgrade the processor. (This computer is about 10 years old.)

---

### Post by d-cosner on 2015-01-10
You can find out what processor it is by using a Ubuntu Live DVD and looking in system details. That heat sink looks like it could use a good cleaning with some compressed air. I can see dust in the fins under the fan.

Edit: Better yet, just look in the system BIOS to see what processor is installed.

Edit 2: It's a socket 939, uses an AMD processor.

---

### Post by mips on 2015-01-11
> **triciasurfer said:**
> QIII, thank you for your reply. I'd like to remove it **so that I could see what chip model is underneath** and upgrade the processor. (This computer is about 10 years old.)


You don't need to remove the heatsink to get the details. Post output of the following commands here,

```
cat /proc/cpuinfo
```

```
sudo dmidecode -t 4
```

```
sudo apt-get install cpuid
cpuid
```

Also include your full **MB make, model, revision & bios version** and we can the give you a list of CPUs that will work.

Remember that if you do remove the heatsink that you would have to clean of all the old thermal paste and replace with new as the old stuff will be rock hard by now, Artic Silver 5 is a good replacement paste.

---

