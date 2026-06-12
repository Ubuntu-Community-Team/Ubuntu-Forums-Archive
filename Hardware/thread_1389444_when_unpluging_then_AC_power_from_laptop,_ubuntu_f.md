---
title: "when unpluging then A/C power from laptop, ubuntu freezes and must be rebooted"
date: 2010-01-24
forum: Hardware
---

### Post by iconoclast88 on 2010-01-24
This happens with no matter what ubuntu linux distro i use. 9.10, 10.4 alpha 2, same result.
I have a new Asus U50F intel i3 from best buy.
Only mepis works without power plugged in.

Also, if i plug in headphones, the audio plays over the speakers AND the headphones at the same time.

Anyone know if this will be addressed in the final release of 10.4 or if there's a way to disable a subsystem like battery management that won't go screwy every time i unplug the power?

Josh

---

### Post by ibuclaw on 2010-01-24
> **iconoclast88 said:**
> This happens with no matter what ubuntu linux distro i use. 9.10, 10.4 alpha 2, same result.
I have a new Asus U50F intel i3 from best buy.
Only mepis works without power plugged in.

Also, if i plug in headphones, the audio plays over the speakers AND the headphones at the same time.

Anyone know if this will be addressed in the final release of 10.4 or if there's a way to disable a subsystem like battery management that won't go screwy every time i unplug the power?

Josh

Will probably need some system info in order to see if it's a known issue.

When you boot the workstation with the AC Power plugged in, run the following in a terminal:
```
dmesg > dmesg.before
```
Then:
```
sync
```
and then unplug the power connector.

Wait about 10 seconds, then press the following key sequence.
Alt+PrintScreen+R
Alt+PrintScreen+E
Alt+PrintScreen+I
Alt+PrintScreen+S
Alt+PrintScreen+U
Alt+PrintScreen+B

Hold down the keys, and wait about 2 seconds between each sequence.
This should ensure that all processes/devices are safely ended/synchronised/unmounted before it reboots your workstation.

When you boot back up again:
```
cat /var/log/dmesg.0 > dmesg.after
```
And attach the two files created to your next post. (They should be dmesg.before and dmesg.after inside your home directory).

Regards
Iain

---

### Post by iconoclast88 on 2010-01-24
thanks for your quick reply.

---

### Post by ibuclaw on 2010-01-24
With the Power Cable plugged in, open a run command box via pressing **Alt+F2**, then paste in the following
```
gksu gedit /etc/default/grub
```
This will prompt you for your password, and open a file.

Locate the following line:
```
GRUB_CMDLINE_LINUX=""
```
and put in:
```
GRUB_CMDLINE_LINUX="**acpi=rsdt**"
```
Save, Quit, then open a terminal and type in:
```
sudo update-grub
```
Then reboot.

Tell us if that makes any difference.

Regards
Iain

---

### Post by iconoclast88 on 2010-01-24
Unfortunately it did not work. Same response when unplugging the power cord from the laptop.

---

