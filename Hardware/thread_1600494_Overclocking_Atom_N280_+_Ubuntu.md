---
title: "Overclocking Atom N280 + Ubuntu"
date: 2010-10-19
forum: Hardware
---

### Post by XAZero on 2010-10-19
Hi all, just a "simple" question regarding overclocking on Ubuntu.
 
I have a HP Mini 311 (nVidia ION (Atom N280 + Geforce 9400M) + 2GB DDR3 (1033MHz)), and after installing Kubuntu 10.10 as it's only OS, I used the hacked BIOS in this thread [http://myhpmini.com/forum/viewtopic.php?f=62&t=3951]("http://myhpmini.com/forum/viewtopic.php?f=62&t=3951") to overclock the Atom CPU from 1.6GHz to 2GHz so KDE would be smoother (it was usable at stock speed but it could be better).

But now it seems that the only way the OC settings can take effect is if the "noapic"(should it be noacpi?) and "acpi=off" arguments are passed to the grub boot command.
cat /proc/cpuinfo reports the speed to be 1000MHz if I dont, and if I do, it correctly reports 2000MHz. (is linux defaulting the FSB?!?)

The draw back is that without acpi a laptop is almost ***unusable*** (i.e. cant sleep).

Any thoughts? 

PS
I do know the risks of OCing, I used Arctic Silver Thermal Paste to enhance The cooling system.

PS2
I used this settings in the BIOS

CPU - 768+32
RAM - 1024+42 unlinked
therefore 
FSB is 800 MHz
Buss is 200 MHz
Core Speed is 2.0 GHz

Thanks

-------------------------------------
gettin SSD and 4 gigs of ram soon :P !!

---

### Post by XAZero on 2010-10-19
bump

---

### Post by XAZero on 2010-10-19
Update

i just realized that /proc/cpuinfo reports the current speed not the maximum speed, so i installed cpufrequtils but regardless it seems that it wont go further than 1.66GHz, probably because of bad ACPI tables... 

Does any one of you know how to modify acpi tables myself?

---

