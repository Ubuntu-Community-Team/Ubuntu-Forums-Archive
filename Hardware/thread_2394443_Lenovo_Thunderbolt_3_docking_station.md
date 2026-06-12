---
title: "Lenovo Thunderbolt 3 docking station"
date: 2018-06-16
forum: Hardware
---

### Post by haeger00 on 2018-06-16
Hello.

I'm quite new to ubuntu, linux in general, and I'm not able to solve the problems with my new Lenovo Thunderbolt 3 docking station.
Neight USB nor the monitor is working and I can't figure why although i might have a trace
After running tail -f /var/log/kern.log i recognized, that it always writes ' thinkpad_acpi: undocked from hotplug port replicator' no matter if i plug or unplug the station.

My system:
Ubuntu version 18.04
PC:
Lenovo Thinkpad x280

I hope someone has a solution.
Thanks

---

### Post by cruzer001 on 2018-06-16
Hello

You did update after you installed?

What about 16.04, it may work out of the box.

[https://certification.ubuntu.com/hardware/201801-26057/](https://certification.ubuntu.com/hardware/201801-26057/)

Possibility Lenovo has the official download.  Maybe try their forum for info on that.

Here is ours
[http://old-releases.ubuntu.com/releases/16.04.1/ubuntu-16.04.1-desktop-amd64.iso](http://old-releases.ubuntu.com/releases/16.04.1/ubuntu-16.04.1-desktop-amd64.iso)
This release will have the LTS kernel already installed.

---

### Post by haeger00 on 2018-06-16
I just ran these:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Didn't help.
I used version 16.04 before, didn't work either

---

### Post by cruzer001 on 2018-06-16
Searching "thinkpad_acpi: undocked from hotplug port replicator" turned up a possible fix.

[https://github.com/martin-ueding/thinkpad-scripts/issues/130](https://github.com/martin-ueding/thinkpad-scripts/issues/130)

---

### Post by haeger00 on 2018-06-16
I also found this site and i followed the steps -> unfortunately no solution

---

### Post by #&amp;thj^% on 2018-06-16
Set one up for a friend of mine>>the trick is in the Bios: [https://forums.lenovo.com/t5/Linux-Discussion/ThunderBolt-3-Dockingstation-and-Linux/td-p/3671481](https://forums.lenovo.com/t5/Linux-Discussion/ThunderBolt-3-Dockingstation-and-Linux/td-p/3671481)

---

### Post by haeger00 on 2018-06-16
Also tried that one...
The only things working are the power button and charging

---

### Post by #&amp;thj^% on 2018-06-16
Something is amiss then, he could actually boot from a drive in the docking station.
The kernel needed has to be higher than 4.10 >> works best with 4.15.
Ubuntu 18.04, and the 9370, 9570 and 9575 all include new enough thunderbolt firmware out of the box.

---

