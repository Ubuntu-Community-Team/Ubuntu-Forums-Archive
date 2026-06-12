---
title: "High temperature HDD on AC"
date: 2009-05-15
forum: Hardware
---

### Post by elw on 2009-05-15
I noticed that my harddisk gets really hot in Ubuntu 9.04. I did a few searches on google and read somewhere that it could have something to do with using the AC power. I ran my laptop 1.5 hours on battery power and the temperature slowly dropped from 50 degrees C to 36 degrees c!

I found this on the internet: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/318346](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/318346)

But apparently it was meant to be fixed in jaunty? But I still have this problem and can't find any solutions.

I know it is still within range but it is too hot for me to work properly with my laptop.
I also noticed that the harddrive sometimes makes a little ticking noise now and then, it never does this on AC power but only does it on battery power.

Does anyone know a solution?

Bit more info:
harddrive: WDC WD2500BEVS-22UST0
Acer Aspire 5720 laptop
The temps on Windows Vista were always around 36 degrees never had this problem.

---

### Post by templarios on 2009-05-15
hello everyone, sorry my English but I speak Italian. I have a similar problem with acer aspire one D150, with AC power the temperature of HDD reaches 55°C.
i use ubuntu 9.04 and acpi-support 0.121
tanks for solution.
bye ;)

---

### Post by elw on 2009-05-16
Anyone?

---

### Post by subever on 2009-06-19
My hdd is getting hot too on ubuntu 9.04 :\ it starts from 51 C, my laptop is really hot, must be a solution to handle this.

---

### Post by tomik76 on 2009-11-08
Compaq Presario C300 with HDD WD800BEVS-60LAT0.
HDD is warmer then on win XP about 10 centigrades on ubuntu (9.04 i 9.10), and on openSuse 11.2 , Load/Unload Cycle 

goes up with similar rate ( 20 per hour or less) at default settings.
If i change them with hdparm -B 253 Load/Unload Cycle skyrockets (150 per hour) but temperature goes down only 2-3 

centigrades, and it is still higher 4-5 centigrades then on XP.
Other lower then 253 settings with hdparm -b don't change anything.
Temperature on **idle** on win XP 39, on Ubuntu 9.10 **50!!!**, under heavy load on XP 43 and on ubuntu and suse 54.

It seams like **WD Scorpio** problem with Linux, I don't know how other drives behave.

Iotop shows that nothing uses disk, i've set noatime and some other settings to keep it idle.

Similar problems also here.
[https://bugs.launchpad.net/ubuntu/+bug/394826](https://bugs.launchpad.net/ubuntu/+bug/394826)
Any ideas?

---

### Post by bianconeri04 on 2009-11-14
Same problems with my Acer laptop, I have a WD3200BVT. On AC power, in idle, it reaches 50 degrees or more. I use ubuntu 9.04.

---

