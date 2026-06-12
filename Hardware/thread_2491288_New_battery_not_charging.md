---
title: "New battery not charging"
date: 2023-10-03
forum: Hardware
---

### Post by nador2 on 2023-10-03
My machine: HP Probook 6560b with actual BIOS. Till now I used Windows 10 64 bit with original 11 years old battery from HP.

Now I switched to Kubuntu 23.04 (in dualboot with Win10). I didnt know if it is just coincidence, but in this moment my battery died (which had still good capacity and was working well, so it was surprise). Windows and Linux wrote "critical error".

Then I bought new unofficial cheap battery, but sufficient according to user ratings in the shop. It came  about 40 percent charged from the shop. I used it and it was written "charging" or "not charging" and then I had to connect the cable few more times to get "charging".. BUT - even there is writen "charging", battery is not charging and percentage is not growing.

in the mean time my Windows shut down badly due to 0% battery so i would have to repair it with installation media which i don't have.. so i can't even test the behavior back in Windows..

Cable looks the same condition as before, so for me it looks that it is not issue of cable or adapter. But I have no other device with which I can confirm it.

_**Now my opinion is that maybe I have incorrect driver for Linux for battery management? **_But I ddint find how to try to update. Or any other ideas how to proceed, what to verify and how? Thank you very much.

```
[FONT=monospace][COLOR=#54ff54]**palu@palu-HP-ProBook-6560b**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/Desktop/hp**[/COLOR][COLOR=#000000]$ upower -i /org/freedesktop/UPower/devices/battery_BAT0 [/COLOR]
  native-path:          BAT0 
  vendor:               Hewlett-Packard 
  model:                Primary 
  serial:               00273 2022/12/01 
  power supply:         yes 
  updated:              Út 3. &#345;íjna 2023, 15:21:11 (8 seconds ago) 
  has history:          yes 
  has statistics:       yes 
  battery 
    present:             yes 
    rechargeable:        yes 
    state:               charging 
    warning-level:       none 
    energy:              0,7659 Wh 
    energy-empty:        0 Wh 
    energy-full:         45,3213 Wh 
    energy-full-design:  45,3213 Wh 
    energy-rate:         0 W 
    voltage:             7,291 V 
    charge-cycles:       N/A 
    percentage:          1% 
    capacity:            100% 
    technology:          lithium-ion 
    icon-name:          'battery-caution-charging-symbolic'

[/FONT]
```

```

[FONT=monospace][COLOR=#54ff54]**palu@palu-HP-ProBook-6560b**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~/Desktop/hp**[/COLOR][COLOR=#000000]$ acpi -V [/COLOR]
Battery 0: Charging, 1%, charging at zero rate - will never fully charge. 
Battery 0: design capacity 4083 mAh, last full capacity 4083 mAh = 100% 
Adapter 0: on-line 
Thermal 0: ok, 25.0 degrees C 
Thermal 0: trip point 0 switches to mode critical at temperature 128.0 degrees C 
Thermal 0: trip point 1 switches to mode passive at temperature 55.0 degrees C 
Thermal 1: ok, 53.0 degrees C 
Thermal 1: trip point 0 switches to mode critical at temperature 128.0 degrees C 
Thermal 1: trip point 1 switches to mode passive at temperature 108.0 degrees C 
Thermal 2: ok, 48.0 degrees C 
Thermal 2: trip point 0 switches to mode critical at temperature 128.0 degrees C 
Thermal 3: ok, 0.0 degrees C 
Thermal 3: trip point 0 switches to mode critical at temperature 128.0 degrees C 
Thermal 4: ok, 60.0 degrees C 
Thermal 4: trip point 0 switches to mode critical at temperature 128.0 degrees C 
Thermal 4: trip point 1 switches to mode hot at temperature 99.0 degrees C 
Thermal 5: ok, 44.0 degrees C 
Thermal 5: trip point 0 switches to mode critical at temperature 128.0 degrees C 
Cooling 0: Processor 0 of 7 
Cooling 1: x86_pkg_temp no state information available 
Cooling 2: Processor 0 of 7 
Cooling 3: Processor 0 of 7 
Cooling 4: intel_powerclamp no state information available 
Cooling 5: Processor 0 of 7

[/FONT]
```

---

### Post by nador2 on 2023-10-03
[[IMG]https://i.ibb.co/mzhpvnm/battery.jpg[/IMG]]("https://imgbb.com/")
"Battery is 1%, charging" - without changes in time...

---

### Post by nador2 on 2023-10-03
Here similar topic, but not much helpful: [https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/Battery-won-t-charge-after-moving-to-Ubuntu-OS/td-p/6135394](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/Battery-won-t-charge-after-moving-to-Ubuntu-OS/td-p/6135394)

---

### Post by #&amp;thj^% on 2023-10-03
On mine, reading the current status
```
 cat /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode

```
Mine now shows 1

Result: 0 = disabled, 1= enabled
Now I'll disable it for testing propose:
```
 sudo bash -c 'echo 0 > /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode'

```
Now shows:
```
cat /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode
0

```
Now I'll re-enable:

```
sudo bash -c 'echo 1 > /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode'
```
Check again:
```
cat /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode
1

```
BTW conservation_mode will charge my battery to %95 for safety of an overcharge.
And you might want to check your Bios for a Battery Setting % to charge to.

I hate being the bearer of bad news, but "compatible" laptop batteries may not be compatible.
Some laptops depend on a chip in the battery for proper functioning.
Best to buy a replacement of the same brand and part number that was originally installed.

---

### Post by Autodave on 2023-10-03
I have been burned several times with "compatible" batteries.  Some never worked, some worked for a few weeks.

---

