---
title: "Problem with i8k (Inspiron 5100)"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by Zerboxx on 2005-07-26
Well lets get down to the facts:
I have a Dell Inspiron 5100, Ubuntu 5.04, and I would like to see the temperature of my cpu (which I was able to do with M$).
I've installed i8kutils (through synaptic) and can't seem to get it working (though delire on #ubuntu has tried to help me quite a lot)
Here are some terminal outputs:
```
jon@lappy486:~$ sudo lsmod | grep acpi
sony_acpi               6280  0
pcc_acpi               11264  0
```
```
jon@lappy486:~$ sudo modprobe -l | grep acpi
/lib/modules/2.6.10-5-386/kernel/drivers/pci/hotplug/acpiphp.ko
/lib/modules/2.6.10-5-386/kernel/drivers/pci/hotplug/acpiphp_ibm.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/video.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/toshiba_acpi.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/thermal.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/sony_acpi.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/pcc_acpi.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/processor.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/fan.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/ibm_acpi.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/button.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/battery.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/container.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/ac.ko
/lib/modules/2.6.10-5-386/kernel/drivers/acpi/asus_acpi.ko
/lib/modules/2.6.10-5-386/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko
```
And this is what I get when I try to do "sudo modprobe i8k"
```
FATAL: Error inserting i8k (/lib/modules/2.6.10-5-386/kernel/drivers/char/i8k.ko): No such device
```
I've removed sony_acpi (as per delire), but sudo modprobe i8k still gives that error.
Any help with this would be greatly appreciated.  Thanks!

---

### Post by Zerboxx on 2005-07-26
I got it working with this command:
modprobe i8k force=1
Thanks din (from #ubuntu)!

---

### Post by floflooo on 2005-09-08
[QUOTE=Zerboxx]I got it working with this command:
modprobe i8k force=1
Thanks din (from #ubuntu)![/QUOTE]
 I needed to force the loading of this module on my D600.

Therefore I just had to add this line at the end of the /etc/modules file to have it automatically loaded at each boot:
> i8k force=1

---

### Post by mlord on 2005-09-09
[QUOTE=Zerboxx]Well lets get down to the facts:
I have a Dell Inspiron 5100, Ubuntu 5.04, and I would like to see the temperature of my cpu (which I was able to do with M$).[/QUOTE]

    cat  /proc/acpi/thermal_zone/THM/temperature

??

---

### Post by fenario on 2007-08-01
Hi Friend

I also have an Inspiron 5100 with the A23 BIOS update(which addressed dust issues and thus stops the fan if not absolutely necessary).
I'm keen on having a look at temps, especially in an Aussie summer.
What did you use in Windows to see temps?
Will try to use i8kutils on ubuntu 7,04. 
greetings from OZ
fenario

---

