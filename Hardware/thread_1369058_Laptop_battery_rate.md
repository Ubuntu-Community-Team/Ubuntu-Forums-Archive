---
title: "Laptop battery rate"
date: 2009-12-31
forum: Hardware
---

### Post by Nagrom_17 on 2009-12-31
I just got a new HP G60-506 for Christmas and I was wondering how I can get stuff like an estimation of battery time left and time until a full charge working. The battery is an EV06047 and I believe the problem is that everywhere I look that has information about the battery it says the rate is 0 which is impossible since then the battery would never run out. So does anyone have an idea of how I can get the battery rate working/if that is not the problem get an estimated time to full charge/discharge. Thank you

---

### Post by sarthorks on 2009-12-31
1.Assuming you have ACPI compiled in your kernel,
type
```
acpi
``` in the terminal.
eg. ```

acpi
     Battery 1: discharging, 60%,  remaining

```

2.install "ibam" from synaptic package manager, then type
```
ibam
``` in the terminal.
eg. ```

 ibam
Battery time left:           1:03:38
Adapted battery time left:   1:03:38

```

3.type
```
cat /proc/acpi/battery
```
and at this point press TAB twice, and it automatically enters something like BAT1 next to .../acpi/battery/
Now press TAB twice again, and you will most probably see files like "alarm", "info", and "state". Enter the names of these files one by one, and press enter. That will give information about the batteries.
eg
```

cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         5100 mAh
last full capacity:      5100 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 420 mAh
design capacity low:     156 mAh
capacity granularity 1:  264 mAh
capacity granularity 2:  3780 mAh
model number:            PA3465U 
serial number:           3658Q
battery type:            Li-Ion
OEM info:                COMPAL 

```
and
```

cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            0 mA
remaining capacity:      3111 mAh
present voltage:         11100 mV

```

---

### Post by Nagrom_17 on 2009-12-31
Awesome now I at least know I can get the time remaining from the terminal, whats the secret for getting that time on the gnome battery monitor though? Or would it be a separate applet?

---

### Post by sarthorks on 2009-12-31
Isn't your Battery Charge Monitor already giving you the stats?
Add it to your panel by right clicking the panel>Add to Panel>Battery Charge Monitor.

---

### Post by Nagrom_17 on 2009-12-31
there is no option of a battery charge monitor under the add to panel window. I have a little grey battery in the top right next to my wifi and that is not showing it yet, maybe i need to reboot or something

---

