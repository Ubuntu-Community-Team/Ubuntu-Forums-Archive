---
title: "Battery has 2%, state is charging but its not charging"
date: 2017-09-02
forum: Hardware
---

### Post by matuszewski-mik on 2017-09-02
Hello,
yesterday I left my laptop with 1-2% battery on desk and let laptop 'die' on desk (i even heard the sound signal about low level battery). When today's morning I plugged AC to laptop, turned on, the indicator shows 2% and that time to full charged battery is calculated... (it's not changing in time). When I remove the cable from the power adapter the laptop turns off immediately. 

Laptop is: HP Probook 450 g3 (11 months old)
Kernel version: 4.10.0-33-generic
Ubuntu version: 16.04 LTS

uppower --dump:
```

Device: /org/freedesktop/UPower/devices/line_power_AC
  native-path:          AC
  power supply:         yes
  updated:              sob, 2 wrz 2017, 13:00:35 (583 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              yes
    icon-name:          'ac-adapter-symbolic'


Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               Hewlett-Packard
  model:                Primary
  serial:               36103 2016/05/20
  power supply:         yes
  updated:              sob, 2 wrz 2017, 13:08:41 (97 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              0,5624 Wh
    energy-empty:        0 Wh
    energy-full:         23,7688 Wh
    energy-full-design:  23,7688 Wh
    energy-rate:         0 W
    voltage:             14,798 V
    percentage:          2%
    capacity:            100%
    technology:          lithium-ion
    icon-name:          'battery-caution-charging-symbolic'


Device: /org/freedesktop/UPower/devices/DisplayDevice
  power supply:         yes
  updated:              sob, 2 wrz 2017, 13:00:35 (583 seconds ago)
  has history:          no
  has statistics:       no
  battery
    present:             yes
    state:               charging
    warning-level:       none
    energy:              0,5624 Wh
    energy-full:         23,7688 Wh
    energy-rate:         0 W
    percentage:          2%
    icon-name:          'battery-caution-charging-symbolic'


Daemon:
  daemon-version:  0.99.4
  on-battery:      no
  lid-is-closed:   no
  lid-is-present:  yes
  critical-action: HybridSleep

```

Can someone help me?

Thanks!

---

### Post by Autodave on 2017-09-02
Possibly your battery has died. I know you said only 11 months old, but it could be bad. Since the laptop works with the AC adapter, at least we know that the adapter appears to still be OK.

Let me give you something to try. It won't cost anything but 10 minutes of your time and it just may fix your issue. I have used this on many laptops and have a good bit of success in doing so (about 50%).

  	 	 	 	   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by matuszewski-mik on 2017-09-02
> **Autodave said:**
> Possibly your battery has died. I know you said only 11 months old, but it could be bad. Since the laptop works with the AC adapter, at least we know that the adapter appears to still be OK.

Let me give you something to try. It won't cost anything but 10 minutes of your time and it just may fix your issue. I have used this on many laptops and have a good bit of success in doing so (about 50%).

                        1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.
Thanks for your replay and help :) but... it didn't work :/

Any other ideas?

---

### Post by Autodave on 2017-09-02
Whatever media you used to install Ubuntu: boot up to that install disc / USB dribe and choose "Try Ubuntu". Do not install it. With the laptop running on that, see if your battery charges then.

---

### Post by matuszewski-mik on 2017-09-03
> **Autodave said:**
> Whatever media you used to install Ubuntu: boot up to that install disc / USB dribe and choose "Try Ubuntu". Do not install it. With the laptop running on that, see if your battery charges then.
no changes on Linux Minut :/ should I try windows?

---

### Post by Autodave on 2017-09-03
If Windows is available, sure! If nothing there, you may need to find a new battery.........

---

### Post by kostkon on 2017-09-05
Isn't the value
```
energy-full:         23,7688 Wh
```
a bit on the low side? Even my 7 year-old netbook's battery still has about 44Wh left (down from 66Wh when new).

---

