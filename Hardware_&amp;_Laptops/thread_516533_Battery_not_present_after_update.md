---
title: "Battery not present after update"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by -Outcast- on 2007-08-03
Hello,

I just updated Gnome Feisty. And my battery icon tells me I do not have a battery installed?!! Acer travelmate 4500. Everything was fine before update.

I have rebooted. Unplugged battery etc. Hardware manager is missing anything to do with the battery.

Windows does recognise it. 

Power saving mode seems to still work?!! If I unplug the power cord the LCD dims. 

Hmmm why would this happen? the updates totalled 128mb so it was quite big. 

I am not an expert and am not used to any command line type debugs but if someone could help me here I would appreciate as I am on the brink of getting rid of Windows altogether.

Thanks

---

### Post by -Outcast- on 2007-09-12
Still hoping for some help on this one guys?!!! ITs driving me mad!!!

---

### Post by qazser on 2007-09-25
Hi

I had the same problem in my Acer TM 4001LMi. I fix it following this [spanish post]("http://www.ubuntu-es.org/index.php?q=node/57972"). The problem happens when you use the 2.6.20-16 kernel. With the 2.6.20-15 the battery is detected and the gnome applet works fine. Check it before with the liveCD. 

It seems the smart battery support has a problem and it don't work.  The solution is quite simple take the battery driver of the 2.6.20-15 kernel and install in the 2.6.20-16. The first step is make the 2.6.20-16 driver back-up.
```
sudo cp /lib/modules/2.6.20-16-generic/kernel/drivers/acpi/i2c_ec.ko /lib/modules/2.6.20-16-generic/kernel/drivers/acpi/i2c_ec.ko.OLD
``` 

and then copy the 2.6.20-15 driver.
```
sudo cp /lib/modules/2.6.20-15-generic/kernel/drivers/acpi/i2c_ec.ko /lib/modules/2.6.20-16-generic/kernel/drivers/acpi/i2c_ec.ko
```

restart the computer and test the detection with
```
acpi -V
```

And that's all I have done.
bye.

---

