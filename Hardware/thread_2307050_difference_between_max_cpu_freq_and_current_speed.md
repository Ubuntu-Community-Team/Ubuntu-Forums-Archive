---
title: "difference between max cpu freq and current speed"
date: 2015-12-21
forum: Hardware
---

### Post by peter186 on 2015-12-21
Hi all. I have underclocked my pc to 3.8 GHz.

There is a strange difference between mas cpu frequency and maximal current speed.

```
sudo dmidecode -t processor | grep Speed
    Max Speed: 3800 MHz
    Current Speed: 4000 MHz
```

Intel Turbo Boost is turned off in BIOS/UEFI.

---

### Post by weatherman2 on 2015-12-21
"Max Speed" is probably the internal bus speed inside the CPU.

On my netbook with its 1.1GHZ Sandy Bridge Celeron CPU, that command gives me this result:

```

	Max Speed: 4000 MHz
	Current Speed: 1100 MHz

```

Clearly my CPU (which doesn't even have turbo boost) can't run at 4GHZ, but the FSB speed is probably that (using DDR3 1066 I think, and its multiplied 4X internally).

---

### Post by peter186 on 2015-12-22
Is seems like these two parameter are not connected to actual CPU settings at all.

---

### Post by P . P . L . on 2015-12-22
> **peter186 said:**
> Is seems like these two parameter are not connected to actual CPU settings at all.

Hi.

Try this to see speed of all threads/cores.

watch -n .2 grep Hz /proc/cpuinfo

---

