---
title: "Bluetooth off at boot and powersave on battery"
date: 2009-11-06
forum: Hardware
---

### Post by linuxopjemac on 2009-11-06
Can someone help me to turn bluetooth of at boot/login ? I don't want to have bluetooth on while running Ubuntu. Another thing is how to have the power settings to "powersave" at boot/login all the time. It now always goes to on demand. I have laptop mode enabled and I have the following code in /etc/laptop-mode/conf.d/cpufreq.conf (MacBook 2,1)


```
CONTROL_CPU_FREQUENCY=1
BATT_CPU_MAXFREQ=slowest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=powersafe
BATT_CPU_IGNORE_NICE_LOAD=1
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=ondemand
LM_AC_CPU_IGNORE_NICE_LOAD=1
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=slowest
NOLM_AC_CPU_GOVERNOR=ondemand
NOLM_AC_CPU_IGNORE_NICE_LOAD=0
```

---

### Post by VirtualTiger on 2009-11-06
You can disable the bluetooth through System/Preferences/Startup Applications.

After I replied earlier, I started thinking about it and realized you were looking at how to turn off the bluetooth dongle in order to save power, not just disable the bluetooth service.  

I came across this file while searching for a way to enable my bluetooth mouse on bootup.

/etc/laptop-mode/conf.d/bluetooth.conf

```
###############################################################################
# Bluetooth settings
# ------------------
#
# If you enable this module, laptop mode tools will enable/disable bluetooth
# depending on the power status of your laptop. Bluetooth uses a considerable
# amount of power (comparable to wireless networking), and disabling it is
# therefore a good idea when you are looking to improve your battery life.
#
###############################################################################

# Control bluetooth?
CONTROL_BLUETOOTH=0

# Enable bluetooth on battery
BATT_ENABLE_BLUETOOTH=0

# Enable bluetooth on AC
AC_ENABLE_BLUETOOTH=1

# Bluetooth interfaces to enable/disable
BLUETOOTH_INTERFACES="hci0"
```

Hope this helps...

---

