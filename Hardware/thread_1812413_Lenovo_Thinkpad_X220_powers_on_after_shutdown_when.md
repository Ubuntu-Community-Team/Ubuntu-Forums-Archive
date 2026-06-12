---
title: "Lenovo Thinkpad X220 powers on after shutdown when on battery"
date: 2011-07-26
forum: Hardware
---

### Post by jeorsch on 2011-07-26
Natty now runs reasonably well on my ThinkPad X220 (4290-W1B). Though when I shutdown when running on battery the notebook immediately powers on again. It is not like when I reboot since then the power LED does not turn off. When on AC the shutdown works as expected.
I am using BIOS version 1.19, kernel version 2.6.38-10.46-generic, and I have the laptop-mode-tools installed.
Has anyone an idea how to fix this issue?

---

### Post by firsttimeuser on 2011-07-27
i have the exact same problem, and i cannot seem to find an answer. 

> **jeorsch said:**
> Natty now runs reasonably well on my ThinkPad X220 (4290-W1B). Though when I shutdown when running on battery the notebook immediately powers on again. It is not like when I reboot since then the power LED does not turn off. When on AC the shutdown works as expected.
I am using BIOS version 1.19, kernel version 2.6.38-10.46-generic, and I have the laptop-mode-tools installed.
Has anyone an idea how to fix this issue?

---

### Post by Mawoon on 2011-07-29
Experiencing the same problem on my thinkpad W520 running Debian Testing. Not sure what the problem is exactly.

Latest installed in aptitude log:
[INSTALL] laptop-mode-tools
[REINSTALL] tp-smapi-dkms
[INSTALL] cpufrequtils

---

### Post by firsm on 2011-09-19
Same issue with a T420 here. As a workaround, you might want to try unloading the following modules prior to shutting down:

 battery
 ac
 power_supply

---

### Post by wimute on 2011-11-02
Same problem on x220 with Ubuntu 11.10

---

### Post by febrile on 2011-12-09
I had the same problem on the Thinkpad X121e(Intel,3045-CTO), solved in this case by unloading the ehci_hcd module on shutdown. May be worth trying on the X220 too ...
With AC unplugged, try:
$ sudo rmmod ehci_hcd && sudo shutdown -h now

If that works then you can put it in the standard shutdown scripts. For example, step-by-step:
$ gksudo gedit /etc/init.d/unload_echi_hcd #and copy/paste the following: 
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          unload_ehci_hcd
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     
# Default-Stop:      0
# Short-Description: Unload ehci_hcd module pre-halt
# Description:       Fix for clean shutdown on battery [Thinkpad X121e]
### END INIT INFO
# Author: HFW
# Purpose: force remove ehci_hcd module for clean shutdown on battery (Thinkpad X121e)

case $1 in
  start|restart|reload|force-reload|status)
    ;;

  stop)
    echo "Unloading module ehci_hcd [ThinkPad fix]."
    rmmod ehci_hcd
    ;;

  *)
    echo "Usage: $0 {stop|start|restart|reload|force-reload}" >&2
    exit 2
    ;;
esac
exit 0
```
$ sudo chmod +x /etc/init.d/unload_ehci_hcd
$ sudo update-rc.d unload_ehci_hcd start 00 0

If at some stage you want to undo this:
$ sudo update-rc.d unload_ehci_hcd remove
$ sudo rm /etc/init.d/unload_ehci_hcd


On my Thinkpad X121e, the same module also prevents successful resume from hibernate, resolved with:
$ sudo echo 'SUSPEND_MODULES="ehci_hcd"' > /etc/pm/config.d/ehci_hcd

Have fun.

---

