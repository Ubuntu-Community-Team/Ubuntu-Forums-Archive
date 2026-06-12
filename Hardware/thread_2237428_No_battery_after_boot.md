---
title: "No battery after boot"
date: 2014-08-01
forum: Hardware
---

### Post by emvoo on 2014-08-01
[COLOR=#000000][FONT=sans-serif]First of all: hi to everyone
[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Problem is: battery monitor doesnt recognize any battery and showing empty and red cross on my laptop dell inspiron 7537.[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Right after reboot:[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]```
upower -dDevice: /org/freedesktop/UPower/devices/line_power_AC[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  native-path:          AC[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  power supply:         yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  updated:              Fri 01 Aug 2014 20:54:10 BST (1846 seconds ago)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  has history:          no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  has statistics:       no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  line-power[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    online:             no[/FONT][/COLOR]


[COLOR=#000000][FONT=sans-serif]Daemon:[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  daemon-version:  0.9.23[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  can-suspend:     yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  can-hibernate:   no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  on-battery:      no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  on-low-battery:  no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  lid-is-closed:   no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  lid-is-present:  yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  is-docked:       no[/FONT][/COLOR]


[COLOR=#000000][FONT=sans-serif]
```[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]But when i plug AC it recognizes the battery[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]```
upower -dDevice: /org/freedesktop/UPower/devices/line_power_AC[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  native-path:          AC[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  power supply:         yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  updated:              Fri 01 Aug 2014 21:27:16 BST (12 seconds ago)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  has history:          no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  has statistics:       no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  line-power[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    online:             yes[/FONT][/COLOR]


[COLOR=#000000][FONT=sans-serif]Device: /org/freedesktop/UPower/devices/battery_BAT0[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  native-path:          BAT0[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  vendor:               Samsung SDI[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  model:                DELL 62VNH3A[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  serial:               1560[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  power supply:         yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  updated:              Fri 01 Aug 2014 21:27:21 BST (7 seconds ago)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  has history:          yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  has statistics:       yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  battery[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    present:             yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    rechargeable:        yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    state:               charging[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    energy:              45.0068 Wh[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    energy-empty:        0 Wh[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    energy-full:         57.72 Wh[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    energy-full-design:  57.72 Wh[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    energy-rate:         0.0148 W[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    voltage:             16.158 V[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    percentage:          77%[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    capacity:            100%[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    technology:          lithium-ion[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  History (charge):[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    1406924838  77.000  charging[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    1406924836  78.000  discharging[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    1406924836  0.000   unknown[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  History (rate):[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    1406924838  0.015   charging[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    1406924836  24.894  discharging[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]    1406924836  0.000   unknown[/FONT][/COLOR]


[COLOR=#000000][FONT=sans-serif]Daemon:[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  daemon-version:  0.9.23[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  can-suspend:     yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  can-hibernate:   no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  on-battery:      no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  on-low-battery:  no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  lid-is-closed:   no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  lid-is-present:  yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  is-docked:       no
```[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]battery is in good condition as on win8 it lasts for like 5 hrs easy[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Any ideas how to fix that?[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]Thanks[/FONT][/COLOR]

---

### Post by greatorety on 2014-10-13
Well, after 2 and a half months it's probably too late to be useful for the OP, but maybe it's gonna help somebody else. I found a solution that worked with my 7537 here: [http://dennis2society.de/main/ubuntu-14-04-doesnt-recognize-laptop-battery-dell-inspiron-15-7537](http://dennis2society.de/main/ubuntu-14-04-doesnt-recognize-laptop-battery-dell-inspiron-15-7537)

In short you have to modify a line in **/etc/default/grub **

from: GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;
to: GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash acpi_osi=Linux&#8221;

then run **sudo update-grub** and reboot

---

