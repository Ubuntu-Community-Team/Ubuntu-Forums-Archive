---
title: "cannot Hibernate HP ProDesk 600 G1 Desktop Mini PC"
date: 2015-06-19
forum: Hardware
---

### Post by didier.cabale on 2015-06-19
[ubuntu 14.04 on HP ProDesk 600 G1 Desktop Mini PC]

Hi all,
What I want is to be able to Hibernate a "HP ProDesk 600 G1 Desktop Mini" PC. Currently, I cannot.
I read this 'HowTo' -> [https://help.ubuntu.com/14.04/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/14.04/ubuntu-help/power-hibernate.html), but this had unfortunately no successful effect, ie my previously opened applications were closed after restart.

Note:
1. I checked that my swap partition was larger than my available RAM.
2. HP assistance confirms that this PC supports hibernation:
[Friday, June 19, 2015 6:49 PM] -- Ramachandran R says:
Yes this unit does support Hibernation.

Is this a known issue?
Does anybody know how to fix it?
Thanks
Didier

---

### Post by weatherman2 on 2015-06-19
Have you changed your swap partition at all since your original installation?  If so, you may need to update the file /etc/initramfs-tools/conf.d/resume (with the current UUID of the swap partition) and then run update-initramfs .

Otherwise - I'm not surprised. Hibernation support has long been tricky in Linux.  Hibernation may work perfectly well in Windows but not in Linux due to driver issues, etc.  I take it that support for hibernation is challenging and time consuming and has not been a high priority for developers.

If suspend/sleep works, can you use that instead? Will this computer always be plugged into the wall?  You may find that power consumption in suspend is not much different than in hibernation.  Even when plugged into the wall but power is "off," (as it would be in hibernation) your power supply will still leak some current - perhaps not much less than when you are suspended.  It may be only 1 or 2 watts difference.

---

### Post by Bucky Ball on 2015-06-19
Welcome. Along the lines of weatherman2 but perhaps a slightly easier place for a newcomer to start. Install Gparted from Software Centre if it's not already installed, launch it, right click on the /swap partition and see if it's on. If 'swapoff', set it to on (in the right click menu). Try hibernate again.

If that works we can help you change the fstab so swap is on at boot.

Report any anomalies or issues if you experience any along the way.

---

### Post by didier.cabale on 2015-06-20
Many thanks for your valuable help.
> **weatherman2 said:**
> Have you changed your swap partition at all since your original installation?  If so, you may need to update the file /etc/initramfs-tools/conf.d/resume (with the current UUID of the swap partition) and then run update-initramfs

No, I did not have to change my swap partition by myself
> **weatherman2 said:**
> I take it that support for hibernation is challenging and time consuming and has not been a high priority for developers.

1. you are right .. I spent quite a lot of time on it.
2. It's a shame it is not considered as high priority

> **weatherman2 said:**
> If suspend/sleep works, can you use that instead? Will this computer always be plugged into the wall?

1. No, the computer is supposed to be unplugged from the power supply, because I use my PC like a laptop -> unplug /plug frequently
2. suspend /sleep works fine, but as long as it says plugged. Ie when unplugged /plugged, then it never retrieves the previous state.

I guess that, according to you, there is not much to do, so .. :(
Anyway, many thanks for your help
Didier

---

### Post by didier.cabale on 2015-06-20
[COLOR=#000000]Many thanks for your valuable help.
[/COLOR]> **Bucky Ball said:**
> Install Gparted from Software Centre if it's not already installed, launch it, right click on the /swap partition and see if it's on.

Since right-click shows the Swapoff option, I guess the swap is On.
see [[IMG]http://s2.postimg.org/qwh0whqmt/Screenshot_from_2015_06_20_10_32_55.jpg[/IMG]]("http://postimg.org/image/qwh0whqmt/")

[COLOR=#000000]Anyway, many thanks for your help[/COLOR]
[COLOR=#000000]Didier[/COLOR]

---

