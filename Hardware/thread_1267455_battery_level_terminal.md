---
title: "battery level terminal"
date: 2009-09-15
forum: Hardware
---

### Post by Esthellin on 2009-09-15
Want to check laptop battery level status from terminal. I have seen a suggestion of installing acpi.
Is there a way to check the battery level without extra programs (eg programs alreayd installed onto the machine)?

---

### Post by lloyd_b on 2009-09-15
> **Esthellin said:**
> Want to check laptop battery level status from terminal. I have seen a suggestion of installing acpi.
Is there a way to check the battery level without extra programs (eg programs alreayd installed onto the machine)?

The "acpi" program is installed as part of the package "acpi", which I think is part of a standard install (type "which acpi" in a terminal window to see if "/usr/bin/acpi" is there).

Other than that, you can look at the file(s) in "/proc/acpi/battery", but without a utility program to translate the info that might be hard to understand.

Lloyd B.

---

### Post by sergiom99 on 2009-09-15
```
$ sudo acpitools
```

Good luck!

---

### Post by Whiffle on 2009-09-15
```

cat /proc/acpi/battery/BAT0/state

```

---

### Post by Esthellin on 2009-09-16
> **Whiffle said:**
> ```

cat /proc/acpi/battery/BAT0/state

```

I just tried this one. It shows the state but not in a human-readable format (eg its in mW and mWh instead of in hours or percentage). Any simple way of converting this?

Funny thing is, I ran file /proc/acpi/battery/BAT0/state, and the file was empty, yet 'cat'ting it gave input. Freaky phantom file contents ;D.

As said in the first post, I don't have/want acpi installed onto the laptop (trying to cut down on file system usage).
I found that apm was originally the program used instead of acpi, and saw that this was installed. But running "apm" in terminal gives "No APM support in kernel", which is throghouly unhelpful.
No searches so far have helped 'adding' support for apm.
The program acpitool was also not installed.

---

### Post by Whiffle on 2009-09-16
I think if you take the "remaining capacity" in mAh, divided by the "design capacity" in cat /proc/acpi/battery/BAT0/info, you'll get a percentage.

---

### Post by Esthellin on 2009-09-16
That gives a percentage of 75% when it should be 100%.
I disconnected the powercord and then:
09:03{~} cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            22509 mW
remaining capacity:      39349 mWh
present voltage:         11340 mV

I did (remaining capacity)/(present rate). that gave me the time remaining in the battery. Still can't get a percentage though.

---

### Post by sudevdev on 2012-09-20
```
upower -i /org/freedesktop/UPower/devices/battery_BAT0| grep -E "state|to\ full|percentage|time"

```
you can try this command in terminal to get deatails of battery 

or may try this to view more details about your battery 

```
upower -i /org/freedesktop/UPower/devices/battery_BAT0
```

[http://sudevshares.blogspot.com/](http://sudevshares.blogspot.com/)

---

