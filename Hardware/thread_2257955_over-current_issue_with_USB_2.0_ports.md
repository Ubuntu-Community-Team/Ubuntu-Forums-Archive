---
title: "over-current issue with USB 2.0 ports"
date: 2014-12-23
forum: Hardware
---

### Post by erwin14 on 2014-12-23
[COLOR=#333333][FONT=UbuntuRegular]My system (on Ubuntu 14.04) is no longer shutting down/restarting/suspending since a problem with all usb 2.0 ports occurred. (all of a sudden all usb 2.0 were without power. Luckily, the usb 3.0 ports are still working) In fact, the system stays stuck on "over-current condition on port 1 and 2" which is very annoying since only prolonged pushing on the power button can shutdown the notebook.[/FONT][/COLOR]
dmesg : 
[  282.314980] hub 2-1:1.0: over-current condition on port 2
[  282.522964] hub 2-1:1.0: over-current condition on port 1
........
[COLOR=#333333][FONT=UbuntuRegular]I already tried adding ehci_hcd.ignore_oc=1 to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grubbut this is of no use. 
I just want it to ignore any faults so that it can shutdown or reboot.[/FONT][/COLOR]

---

### Post by tgalati4 on 2014-12-24
Look inside the USB ports with a flashlight.  A bent wire, or dirt could be shorting them out.  If the ports are shorted, then the ACPI system which is the BIOS control of power will be unhappy.

You can turn off power to the USB ports using the *acpitool*.

```
sudo apt-get install acpitool
acpitool -w
```

---

### Post by dimitrov-c on 2015-04-07
Hello, 
I have the same issue with Ubuntu 14.04.2, and only with it. I have no problems with Windows.
I have even tried Ubuntu 12.04, but it revealed other serius bugs (for me), so naw I am on 14.04.2 again and on every boot I have that error message. 
What I think is that this is not a hardware problem, but a bug or something in Ubuntu itself. I have a Nvidia optimus tecnology
which is a pain with linux.

---

### Post by tgalati4 on 2015-04-07
Are you getting the error message with nothing plugged into the USB ports?

Welcome to the forums.

---

### Post by dimitrov-c on 2015-04-13
I think I have found the source of the problem. As I mentioned before I have intel+nvidia graphics, and, as I install the Nvidia proprietary drivers I get this error at reboot. Now I am pretty sure there is a bug within Nvidia drivers, or something. So I removed them and installed Noveau instead and then the error message was gone.
However there is another issue: Noveau doesn't work well on my machine with bumblebee, so I have only the discrete card working. :(

---

