---
title: "Battery Not Charging"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by neilcavendish on 2007-02-14
Hi all. I have set up Ubuntu on my laptop and it works great with a few probs. The main prob i have is that i cant use my laptop with out being pluged into the AC. 

I cant see why i cant charge and use my battery it works on windows. Maybe i am missing something in the kernal. Can anyone help.

Here is some information about my battery.

```

 acpi -b
     Battery 1: charging, 0%, charging at zero rate - will never fully charge.

```

```
neil@NeilLappy:~$ cat /proc/acpi/battery/BAT0/state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            0 mA
remaining capacity:      0 mAh
present voltage:         13525 mV
neil@NeilLappy:~$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         3600 mAh
last full capacity:      2798 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 2768 mAh
design capacity low:     100 mAh
capacity granularity 1:  1 mAh
capacity granularity 2:  1 mAh
model number:            G553
serial number:           1
battery type:            LION
OEM info:                ECS Cop. 

```

As you can see it is just not charging. I thought it was the battery so i got a brand new one and it has the same problem. When it was in the shop it was tested with windows and worked fine. Please help. Thanks in advance.

---

### Post by newstor on 2007-03-10
Same problem here, but in my case it's been working fine for months and all of a sudden it has stopped working :confused:, something is wrong with the power management...

---

