---
title: "missing fan controls on Lenovo Legion Y740, Ubuntu 20.04"
date: 2020-08-25
forum: Hardware
---

### Post by gsync on 2020-08-25
Details:
[LIST]
[*]Lenovo Legion Y740 with RTX 2070 Max-Q
[*]Ubuntu 20.04
[/LIST]

OS don't have a default module that can work with the laptop fans:

```

$: sensors

iwlwifi_1-virtual-0
Adapter: Virtual device
temp1:        +46.0°C


coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +54.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +52.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +52.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +54.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +53.0°C  (high = +100.0°C, crit = +100.0°C)
Core 4:        +50.0°C  (high = +100.0°C, crit = +100.0°C)
Core 5:        +51.0°C  (high = +100.0°C, crit = +100.0°C)


pch_cannonlake-virtual-0
Adapter: Virtual device
temp1:        +58.0°C


BAT1-acpi-0
Adapter: ACPI interface
in0:          12.93 V


&#10140;  AutoSTR git:(master) &#10007;
&#10140;  AutoSTR git:(master) &#10007; sensors
iwlwifi_1-virtual-0
Adapter: Virtual device
temp1:        +46.0°C


coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +53.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +52.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +53.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +53.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +53.0°C  (high = +100.0°C, crit = +100.0°C)
Core 4:        +51.0°C  (high = +100.0°C, crit = +100.0°C)
Core 5:        +52.0°C  (high = +100.0°C, crit = +100.0°C)


pch_cannonlake-virtual-0
Adapter: Virtual device
temp1:        +58.0°C


BAT1-acpi-0
Adapter: ACPI interface
in0:          12.92 V



```

Even after **sensors-detect, **result is still the same.

The system is keeping it's temp close to normal 50-60 degrees Celsius.
But I think it's controlled by the BIOS and I hate that only one of the two fans is working.
I'd like to be able to completely control fans speed in order to lower the temp when laptop is plugged to power source.

---

### Post by CelticWarrior on 2020-08-25
The temperatures are perfectly fine. The firmware alone - UEFI, not BIOS - its doing its job as designed. 
I really don't understand why some people are convinced they know more than the engineers that make they're stuff.

---

### Post by Autodave on 2020-08-25
60 celsius is great: especially for a laptop.  My desktop with RTX 2070 stays at 65 just about all the time.  Even under heavy stress, the fans will both run occasionally,  but normally only one is running.

---

### Post by CelticWarrior on 2020-08-25
> **Autodave said:**
> Even under heavy stress, the fans will both run occasionally,  but normally only one is running.

Exactly. It's working as designed.
If only one is needed to cool it down to the target temperature then only one will be running. Doing otherwise results in wasting energy and increased noise for absolutely no reason at all.

---

### Post by Yellow Pasque on 2020-08-25
Laptops don't use generic PWM (i.e. something that can be controlled by user with fancontrol script).

---

### Post by gsync on 2020-08-25
> **CelticWarrior said:**
> The temperatures are perfectly fine. The firmware alone - UEFI, not BIOS - its doing its job as designed. 
I really don't understand why some people are convinced they know more than the engineers that make they're stuff.

I'm not convinced I know more then other colleagues.
But I would like to have full control and utilize resources when needed.


The temperature it's fine - yes I agree,
but when you have to sit all day with your hands on the laptop,
and the machine is running with this temperature,
though you have a power supply connected, it ain't fun.
Especially in the summer !

---

### Post by Yellow Pasque on 2020-08-25
It's a gaming laptop with 115W GPU and high-end CPU. Keeping it cool to the touch might be a little unrealistic..

Do you have the Nvidia GPU disabled when you're not gaming or doing intense 3D? That's probably about the only thing you're going to be able to do to cool it down (not counting laptop cooling pads and such).

---

### Post by Autodave on 2020-08-25
You probably get more heat from the CPU than the GPU.

I have a laptop here with just onboard graphics and it gets quite hot just sitting here turned on and doing much of nothing.

If anything, I would get a laptop cooling pad for it.

---

### Post by gsync on 2020-08-25
> **Yellow Pasque said:**
> It's a gaming laptop with 115W GPU and high-end CPU. Keeping it cool to the touch might be a little unrealistic..

Do you have the Nvidia GPU disabled when you're not gaming or doing intense 3D? That's probably about the only thing you're going to be able to do to cool it down (not counting laptop cooling pads and such).

It's not unrealistic when you're running Windows, because you can configure the RPM's of each fan.

But we all know that development under Windows is complete disaster.

What I'm trying to say is that the laptop doesn't need additional cooling pads.
All I need is more control over the fans.
If I can enable both of them it'll provide better airflow out through the chassy.

---

### Post by Yellow Pasque on 2020-08-25
> t's not unrealistic when you're running Windows, because you can configure the RPM's of each fan.

And how do you do that? Proprietary program, right?

---

### Post by gsync on 2020-08-25
> **Yellow Pasque said:**
> And how do you do that? Proprietary program, right?

Yep - it's some Lenovo application.

---

### Post by Yellow Pasque on 2020-08-25
Other than "thinkfan" program, I don't have any suggestions.

---

### Post by Yellow Pasque on 2020-08-25
Well, one other idea that came to me is trying to use Nvidia's "Coolbits" option to see if that will allow you to control the GPU fan. I have no idea if that's supposed to work on a laptop.

It's probably best to use nvidia 450.xx driver if you're going to try that: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=focal](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=focal)
[https://wiki.archlinux.org/index.php/NVIDIA/Tips_and_tricks#Enabling_overclocking](https://wiki.archlinux.org/index.php/NVIDIA/Tips_and_tricks#Enabling_overclocking) (In other words, you'd want to use a value of '4' for Coolbits)

---

