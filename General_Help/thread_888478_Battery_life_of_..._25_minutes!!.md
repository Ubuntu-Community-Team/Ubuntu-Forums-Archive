---
title: "Battery life of ... 25 minutes!!"
date: 2008-08-13
forum: General Help
---

### Post by antm88 on 2008-08-13
Hey,
Basically something is completely eating the CPU on my laptop, can someone recommend a way of discovering what it is? System monitor doesn't reveal much apart from both CPUs at 30% almost all the time.
The fan on my laptop is constantly on full power!
How can I view ALL the processes being launched at startup?
Ant

---

### Post by mali2297 on 2008-08-13
In a terminal, launch
```

top

```
(Press 'h' to see help.)

---

### Post by sayakb on 2008-08-13
At a terminal, do:
```
sudo apt-get install powertop
sudo powertop
```
 
Notice the warnings it issues at the bottom and follow the instructions to fix them.

---

### Post by lisati on 2008-08-13
> **antm88 said:**
> Hey,
Basically something is completely eating the CPU on my laptop, can someone recommend a way of discovering what it is? System monitor doesn't reveal much apart from both CPUs at 30% almost all the time.
The fan on my laptop is constantly on full power!
How can I view ALL the processes being launched at startup?
Ant

You think 25 minutes is bad? Try 5 minutes if I'm lucky!

---

### Post by antm88 on 2008-08-13
> **LinuxIsInnovation said:**
> At a terminal, do:
```
sudo apt-get install powertop
sudo powertop
```
 
Notice the warnings it issues at the bottom and follow the instructions to fix them.
```

  66.5% (213.2)       <interrupt> : extra timer interrupt 
  15.2% ( 48.8)         nm-applet : schedule_timeout (process_timeout) 
   3.8% ( 12.3)       <interrupt> : b43 
   3.5% ( 11.1)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   3.4% ( 11.0)       <interrupt> : libata 
   2.4% (  7.6)           firefox : futex_wait (hrtimer_wakeup)
```

was the output, is there anything abnormal there?

---

### Post by sayakb on 2008-08-13
Look at the bottom where it warns of certain events and ways to change them. For example, it may warn that *USB auto suspend is disabled. Press U to enable it.*

---

### Post by antm88 on 2008-08-13
Sample of my dmesg... this really doesn't look normal!
```
[ 1273.678601] APIC error on CPU1: 40(40)
[ 1273.682294] APIC error on CPU0: 40(40)
[ 1398.811451] APIC error on CPU0: 40(40)
[ 1398.807462] APIC error on CPU1: 40(40)
[ 1422.195601] APIC error on CPU1: 40(40)
[ 1422.199957] APIC error on CPU0: 40(40)
[ 1482.908426] APIC error on CPU0: 40(40)
[ 1482.903712] APIC error on CPU1: 40(40)
[ 1517.704681] APIC error on CPU1: 40(40)
[ 1517.709438] APIC error on CPU0: 40(40)
[ 1557.928855] APIC error on CPU1: 40(40)
[ 1557.933823] APIC error on CPU0: 40(40)
[ 1582.953899] APIC error on CPU0: 40(40)
[ 1582.948837] APIC error on CPU1: 40(40)
[ 1620.776112] APIC error on CPU0: 40(40)
[ 1620.770872] APIC error on CPU1: 40(40)
[ 1812.514211] tun0: Disabled Privacy Extensions
[ 1830.782958] APIC error on CPU0: 40(40)
[ 1830.777276] APIC error on CPU1: 40(40)
[ 2062.090499] APIC error on CPU1: 40(40)
[ 2062.097083] APIC error on CPU0: 40(40)
[ 2111.183491] APIC error on CPU1: 40(40)
[ 2111.190304] APIC error on CPU0: 40(40)
[ 2175.522875] b43-phy0 ERROR: PHY transmission error
[ 2237.404419] tun0: Disabled Privacy Extensions
[ 2267.427378] APIC error on CPU1: 40(40)
[ 2267.435030] APIC error on CPU0: 40(40)
[ 2336.014499] APIC error on CPU0: 40(40)
[ 2336.006495] APIC error on CPU1: 40(40)
[ 2394.597701] APIC error on CPU1: 40(40)
[ 2394.605380] APIC error on CPU0: 40(40)
[ 2405.815190] APIC error on CPU0: 40(40)
[ 2405.807728] APIC error on CPU1: 40(40)
[ 2718.031751] APIC error on CPU0: 40(40)
[ 2718.026363] APIC error on CPU1: 40(40)
[ 2749.366783] APIC error on CPU0: 40(40)
[ 2749.361455] APIC error on CPU1: 40(40)
[ 2787.351507] APIC error on CPU1: 40(40)
[ 2787.356827] APIC error on CPU0: 40(40)
[ 2805.642948] APIC error on CPU1: 40(40)
[ 2805.648235] APIC error on CPU0: 40(40)
[ 2907.562047] b43-phy0 ERROR: PHY transmission error
[ 2922.626351] APIC error on CPU0: 40(40)
[ 2922.620170] APIC error on CPU1: 40(40)
[ 2974.233775] b43-phy0 ERROR: PHY transmission error
[ 3007.647672] APIC error on CPU0: 40(40)
[ 3007.641171] APIC error on CPU1: 40(40)
[ 3037.831185] APIC error on CPU1: 40(40)
[ 3037.837749] APIC error on CPU0: 40(40)
[ 3203.945641] APIC error on CPU0: 40(40)
[ 3203.937727] APIC error on CPU1: 40(40)
[ 3270.086343] APIC error on CPU0: 40(40)
[ 3270.078072] APIC error on CPU1: 40(40)
[ 3461.443051] APIC error on CPU0: 40(40)
[ 3461.434115] APIC error on CPU1: 40(40)
[ 3655.374767] APIC error on CPU0: 40(40)
[ 3655.365391] APIC error on CPU1: 40(40)
[ 3662.473562] APIC error on CPU1: 40(40)
[ 3662.482969] APIC error on CPU0: 40(40)
[ 3765.384174] APIC error on CPU0: 40(40)
[ 3765.374881] APIC error on CPU1: 40(40)
[ 3900.397975] usbcore: deregistering interface driver hci_usb
[ 3937.552826] APIC error on CPU0: 40(40)
[ 3937.543121] APIC error on CPU1: 40(40)
[ 4006.973155] APIC error on CPU1: 40(40)
[ 4006.982979] APIC error on CPU0: 40(40)
[ 4037.806467] APIC error on CPU0: 40(40)
[ 4037.796728] APIC error on CPU1: 40(40)

```

---

### Post by sayakb on 2008-08-13
I am not on my ubuntu box right now, so I may not be accurate at this. Press Alt+F2 and type in **gconf-editor**. Navigate to /apps/gnome-power-manager and there should be cpu_freq options for battery ann ac. Reduce the frequency percentage for battery mode. This should save some power.

---

