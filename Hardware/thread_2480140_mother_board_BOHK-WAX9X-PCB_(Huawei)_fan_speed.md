---
title: "mother board BOHK-WAX9X-PCB (Huawei) fan speed"
date: 2022-10-20
forum: Hardware
---

### Post by luca-dgh on 2022-10-20
I have a Huawei MateBook D15 with Ryzen 5, currently running Ubuntu Mate 22.04 with Kernel 5.15.0-52.
I have some free time so I want try to detect the fan speed, I know that it is quite complicated, but I love challenges. On the web there is no documentation, so could someone help me to understand what software I need?

---

### Post by Bashing-om on 2022-10-20
luca-dgh - Hello :D

> 
I know that it is quite complicated

Well, no - Ubuntu is of the philosophy that if it is hard ----> you are doing something wrong :D

Consider that ubuntu has been around for a while and most anything that you can think of has been thought of.
We have the tool: lm-sensors - " utilities to read temperature/voltage/fan sensors". I understand that support for the Ryzen CPUs are now available within the later kernels.

Please see in terminal the result of the command:
```

apt show lm-sensors

```

I seem to recall that lm-sensors is installed in ubuntu by default - 
check:
```

dpkg -l lm-sensors

```

-^ a fine place to start the process-

---

### Post by luca-dgh on 2022-10-21
Hi Bashing-om, thx a lot for your reply.
lm-semsors is default installed on Ubuntu, it can detect the thermal sensors for CPU, GPU, SSD drive and battery voltage and charge, but it can't detect the fan. 
I know that fan speed detection it's quite a problem in Linux because the IT87 driver (I hope that was the right name, don't remember) is discontinued.

---

### Post by luca-dgh on 2022-10-21
This is my sensors output

```
luca@laptop-luca:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
Tctl:         +32.9°C  

nvme-pci-0100
Adapter: PCI adapter
Composite:    +31.9°C  (low  = -273.1°C, high = +83.8°C)
                       (crit = +84.8°C)
Sensor 1:     +31.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +28.9°C  (low  = -273.1°C, high = +65261.8°C)

amdgpu-pci-0300
Adapter: PCI adapter
vddgfx:           N/A  
vddnb:            N/A  
edge:         +33.0°C  

BAT1-acpi-0
Adapter: ACPI interface
in0:          11.91 V  
curr1:       459.00 mA 

```

---

### Post by Bashing-om on 2022-10-21
luca-dgh  - yuk


Well well well ... Next up then is:
[https://wiki.archlinux.org/title/fan_speed_control](https://wiki.archlinux.org/title/fan_speed_control)
for lm-sensors >>
But do head the warnings and exercise the due care.

-not giving up yet-

---

### Post by luca-dgh on 2022-10-30
Thx Bashing-om, but that page of Arch wiki assume that the kernel has the it87 driver installed, but my problem is that the driver currently is not inserted in the Kernel.
That is the big problem.

---

### Post by Bashing-om on 2022-10-31
luca-dgh; Hummm ...

what driver gets loaded at boot time ?
```

less /etc/modules

```

I do not recall right off the top of my head how one verifies the correct driver. Will take a bit of research on our part to re-learn what I do not recall :(

[INDENT]progress - one step at a time
[/INDENT]

---

