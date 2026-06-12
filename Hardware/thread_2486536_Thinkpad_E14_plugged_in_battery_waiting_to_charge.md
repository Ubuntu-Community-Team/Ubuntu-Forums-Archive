---
title: "Thinkpad E14 plugged in battery waiting to charge"
date: 2023-05-03
forum: Hardware
---

### Post by smith73 on 2023-05-03
There is a new Lenovo ThinkPad E14 gen2 (AMD Ryzen 3 4300U with Radeon Graphics × 4 ) with integrated Li-Polymer 45Wh battery with Windows 10/Ubuntu 22 dual boot.
During the first month of plugged in usage the battery showed 100%/charging and if slightly discharged, the red light indicator near the USB-C
charging port was active before full charge (which is indicated by the white light).
Now the light indicator near the USB-C charging port is always white and the battery icon shows 94%, waiting to charge while plugged into the AC.

The **upower -e** and the subsequent **upower -i /org/freedesktop/UPower/devices/battery_BAT0 **show the following:

native-path:          BAT0
  vendor:               Celxpert
  model:                5B10X026
  serial:               1305
  power supply:         yes
  updated:              Wed 03 May 2023 06:24:28 PM EEST (26 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               pending-charge
    warning-level:       none
    energy:              42.36 Wh
    energy-empty:        0 Wh
    energy-full:         44.67 Wh
    energy-full-design:  45 Wh
    energy-rate:         1.528 W
    voltage:             11.578 V
    charge-cycles:       3
    percentage:          94%
    capacity:            99.2667%
    technology:          lithium-polymer
    icon-name:          'battery-full-charging-symbolic'

The official Lenovo *User Guide* for this ThinkPad mentiones the following:
"Battery charging is also affected by the battery temperature. The recommended battery temperature range
for charging the battery is between 10°C (50°F) and 35°C (95°F).
Note: To maximize the life of the battery, once the battery is fully charged it must discharge to below 95%
before it will be allowed to recharge again."
Also it recommends using the battery until the charge is depleted to maximize battery life.

I have never done that because I was always plugged in and didn't need to use the laptop on battery only.

Some tutorials from Google first page mentioned protecting the laptop from electrostatic discharge, and this issue apparently
appeared after I had been leaving the powered off laptop with the opened lid overnights covered with a piece of cloth
(a possible electrostatics accumulator) and with the internet cable also plugged into the port, though with the AC
power plugged out.

Some tutorials recommend to dismantle the battery (after optionally pressing the power button for 30 seconds)
and assemble it again to reinitialize it. It seems like not a big deal, but the laptop is under warranty and I am wary of any
~stickers inside showing the attempts to tamper with the hardware. Though the hardest thing for me would be to
 safely remove the bottom casing without scratches, but it would only worth it if I'd be sure this will work.

I also checked the *Lenovo Diagnostics tool *from BIOS Setup menu and run all the battery tests, which have been passed
and the Diagnostics tool showed that the battery is ok.
So it seems as some software problem, as I am always using the laptop plugged in and the battery constantly shows 94%/waiting to charge.

A tutorial recommends using the **auto-cpufreq** tool ([https://github.com/AdnanHodzic/auto-cpufreq](https://github.com/AdnanHodzic/auto-cpufreq)) in balanced mode (--install)
 instead of Turbo boost, but I suppose I don't have Turbo boost in this Ubuntu distro and don't use it. The auto-cpufreq tool should 
override the current ubuntu power management app.

The Lenovo *Hardware Maintenance Guide* also indicates to disable builtin battery in BIOS Setup menu before servicing.
But how would I boot into BIOS again to enable it if it will be disabled in BIOS Setup?

What can I do apart from installing auto-cpufreq on Ubuntu to make the battery show 100%/charging?
Do I really need to disassemble and reassemble the battery?

---

