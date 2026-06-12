---
title: "abnormal exit errors on 9.04 install"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by lievenv on 2009-04-27
Hi all,

I'm fairly new to Linux, but I decided to give Jaunty Jackalope a go.
I succeeded at installing the OS from a boot cd, then i'm told to reboot the machine and on reboot I get a bunch of abnormal exit errors:

export /dev/block/1:11
/devicces/virtual/block/ram2
export /dev/block/1:2
/devices/virtual/block/ram5
export /dev/block/1:5
/devices/virtual/block/ram8
export /dev/block/1:8
/devices/virtual/input/mice
/devices/virtual/input/input3/mouse0

I'm trying to install on a compaq armada m700 P3 650 MHz with 448MB ram and a 80gig EIDE harddrive.

Any thoughts?

Thanks!
V

---

### Post by lievenv on 2009-04-27
Ok, so I rebooted in repair mode (or something) and after a few screens of text (too fast to read), it stopped on

path_id /devices/platform/i8042/serio4/input/input6/event6 abnormal exit

Sorry to be such a noob about this.
I really want to give ubuntu a try as an alternative to windows, but I just can't seem to get it installed...
sigh...
V

---

### Post by lievenv on 2009-04-27
Also the "try ubuntu without making any changes to your system" freezes on loading...

---

### Post by lievenv on 2009-04-27
Next I tried installing with everything off:
acpi
apci
cpia
and whatelse not ;-)
Also in safe graphics mode (or whatever it was called).
Still to no avail...
This time I got:
udevd-event [2303]: '/sbin/modprobe -b pci:v0000125Dd00001978sv0000E11sd0000B112bc04sc01i00' abnormal exit

any thoughts...

anyone?

---

### Post by daveyforeal on 2009-05-06
same situation on an armada e500

---

### Post by tute on 2009-06-01
Same with xubuntu 9.04 on a Compaq, PII 500MHz, 380MB RAM.

---

### Post by tute on 2009-06-02
Ubuntu 8.10 worked good, but after updating to 9.04, it didn't boot anymore.

Commented out latest kernel in /boot/grub/menu.lst (2.6.28-11), and now with kernel version 2.6.27-14 it works fine.

Regards.

---

### Post by tute on 2009-06-08
Doesn't work neither on an Armada E500! How may I install an earlier kernel? Ubuntu doesn't fit in 100MB of RAM...

---

### Post by MastarPete on 2009-06-09
> **tute said:**
> Ubuntu 8.10 worked good, but after updating to 9.04, it didn't boot anymore.

Commented out latest kernel in /boot/grub/menu.lst (2.6.28-11), and now with kernel version 2.6.27-14 it works fine.

Regards.

I experienced basically the same thing with an Armada m700 (P3 500mhz ~256mb ram) though I just used the grub boot menu. I was able to occasionally boot when I moved the hard drive into a 1ghz m700 with 576mb ram. I forget if I tried just moving the ram from the 1ghz to the 500. Either way I was able to boot consistently using the previous kernel.

at least I'm not the only one having trouble :???:

---

### Post by ximhot on 2009-08-23
It happened to my M700 when I upgraded from 8.10 to 9.04. Says "Segmentation fault" and hung during booting. 

I reversed to 8.04.3 LTS just in case.

I guess it is the kernel that is not supporting Armada motherboard.

:confused:

---

### Post by thijsz on 2009-09-29
same issue here : armada laptop freezes whe i try to boot from the xubuntu 9.04 live/install cd
i'll give it a go with a previous ubuntu version, see what happens
i've also tried several different boot options (the acpi options) but no luck
 
will try one more time to see what the bootlog says
 
ciao
Thijszz

---

