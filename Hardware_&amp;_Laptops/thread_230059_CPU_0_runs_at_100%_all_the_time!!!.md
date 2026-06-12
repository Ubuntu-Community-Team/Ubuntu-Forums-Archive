---
title: "CPU 0 runs at 100% all the time!!!??"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by BKK on 2006-08-05
I have just noticed that CPU 1 runs at 100% all the time and that CPU 2 runs at around 8%.

I am only using firefox and have the system monitor open.

What can I check to see the cause of this?

I have just done the updates I am running 686-smp kernel

Thanks

---

### Post by gesho on 2006-08-05
[http://www.ubuntuforums.org/showthread.php?t=186003](http://www.ubuntuforums.org/showthread.php?t=186003)

check this out, mostly last pages about acpi timer bug and fix

---

### Post by BKK on 2006-08-05
Very strange....when I rebooted the notebook this morning things are back to normal. I mean I am doing the exact same things I was when I had the problem of cpu1 running 100%!

---

### Post by BKK on 2006-08-05
Reading through the forums here I have found some other weird things...
Could someone explain these for me?

@ubuntu:~$ cat /proc/acpi/processor/CPU0/power
active state:            C2
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00138989]
    C3:                  type[C3] promotion[--] demotion[C2] latency[057] usage[00859887]

ubuntu:~$ cat /proc/acpi/processor/CPU1/power
active state:            C3
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
    C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00144396]
   *C3:                  type[C3] promotion[--] demotion[C2] latency[057] usage[01756732]

This one is strange to me...@ubuntu:~$ acpi -t
     Battery 1: charged, 100%
     Thermal 1: ok, 46.0 degrees C
     Thermal 2: ok, 0.0 degrees C

@ubuntu:~$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes
@ubuntu:~$ cat /proc/acpi/processor/CPU1/info 
processor id:            1 
acpi id:                 1
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes

---

