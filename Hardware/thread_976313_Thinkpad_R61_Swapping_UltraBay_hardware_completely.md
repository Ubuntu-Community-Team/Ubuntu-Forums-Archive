---
title: "Thinkpad R61: Swapping UltraBay hardware completely freezes system"
date: 2008-11-09
forum: Hardware
---

### Post by Franko30 on 2008-11-09
Hi,

I use a Lenovo Thinkpad R61 with 8.04 (all updates applied as of the day of writing this message).

Everything works really fine as described in
[https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadR61](https://wiki.ubuntu.com/LaptopTestingTeam/ThinkpadR61)
except the UltraBay:

When taking out the UltraBay DVD drive, Ubuntu completely freezes (not even accepting keyboard commands anymore for console switches, have to power off via pressing power button for a longer time).

Does anybody know how to solve this or simply "software eject" the UltraBay hardware before removing it?

Thanks

Franko30

---

### Post by Franko30 on 2008-11-09
Hi again,

I found some more threads concerning this issue I didn't find before as I searched for "multibay" instead of "UltraBay" ](*,)

The results are:

[LIST=1]
[*]Unmount any DVDs still in the drive (for instance via right click in nautilus)
[*]Find out your scsi-hardware number for the UltraBay DVD by entering ```
ls /sys/class/scsi_device/
``` in a terminal.
[*]Open a root terminal (ore use "sudo su" in a normal terminal)
[*]Enter ```
echo 1 > /sys/class/scsi_device/[COLOR="Blue"]X[/COLOR]:0:0:0/device/delete
``` where "[COLOR="Blue"]X[/COLOR]" is one of the numbers you saw in step 2.
[*]Use the release and eject buttons/levers on your UltraBay device to eject it. If your system system still freezes, uyou used the wrong number for "[COLOR="Blue"]X[/COLOR]" - reboot and start again.
[/LIST]

After that I can change to my UltraBay battery (which doesn't need to be "software ejected" before removing it again). Subsequently exchanging the batetry for the DVD works fine - the hardware is auto-detected and mounted (if a DVD is in the drive).

The steps above can be written to a script and put into the panel as "click-run-in-a-terminal-and-enter-password" solution. Don't forget to change the terminal's behaviour to "staying open after command is executed" in its profile settings.

Cheers

**Franko30**

Used threads:

[LIST]
[*]The bug (solved in 8.10): [https://bugs.launchpad.net/ubuntu/+bug/242638](https://bugs.launchpad.net/ubuntu/+bug/242638)
[*]No working solution: [http://ubuntuforums.org/showthread.php?t=966705](http://ubuntuforums.org/showthread.php?t=966705)
[*]The thread I got my working lines from: [http://ubuntuforums.org/showthread.php?t=750480](http://ubuntuforums.org/showthread.php?t=750480)
[/LIST]

---

