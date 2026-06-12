---
title: "Fan not working in Karmic"
date: 2009-12-12
forum: Hardware
---

### Post by tw33 on 2009-12-12
I am so close to having karmic working perfectly on this laptop. The only thing isn't working is the fan. It is currently on at the lowest speed and switches off if I suspend.
I wish I could do one of the following:
1. Turn the fan on full - I don't care how loud it is, anything is better than Vista.
2. Disable acpi control of the fan (e.g acpi=off) but still enable suspend.
3. Control the fan properly, enable trip_points, keep the temperature below 60, etc.
Currently if I use the CPU too much it overheats and switches off.

Here is some information:
Xubuntu: Karmic
Laptop: Toshiba Satellite Pro L300D-11L
Processor: AMD Athlon X2 QL-60 64
uname -a: Linux laptop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux
dmesg | grep acpi : [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=bf1b354b-a7c3-4af7-8baa-66a0a0590f7d ro acpi_osi=force quiet splash
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=bf1b354b-a7c3-4af7-8baa-66a0a0590f7d ro acpi_osi=force quiet splash
[    2.557583] acpi device:04: registered as cooling_device3
(I have tried acpi_osi=Linux and acpi=force. acpi=off made the fan worked perfectly, however I could not suspend)
sensors: acpitz-virtual-0
Adapter: Virtual device
temp1:       +67.0°C  (crit = +105.0°C) 
cat /proc/acpi/fan/*/*:
state:                   off
cat /proc/acpi/thermal_zone/THZN/*:
0 - Active; 1 - Passive
<polling disabled>
state:                   ok
temperature:             69 C
critical (S5):           105 C

I updated the BIOS. I got the newest fglrx driver from ATI. Is there anything else I can try?
Thanks so much in advance for helping. Absolutely any suggestions would be much appreciated. Cheers.

---

### Post by s3MA00RRNY on 2009-12-12
Install i8kutils and then read up on how to configure it. I'm not sure if it's only for Dell laptops though.

---

### Post by H4F on 2009-12-12
you forgot to say what laptop you've got ?
I had similar problem with Acer Aspire 5720 . bun once I cleaned it I had no problems.

I have an issue that fun starts working from 45 degree on. with increase of speed if temp goes up.

but it is working on the lowest speed aswell when under 40 degree. so it's annoing me.

---

### Post by tw33 on 2009-12-13
It is a Toshiba Satellite Pro L300D-11L.
From the log line:
acpi device:04: registered as cooling_device3
Surely there must be some way I can control it?
How can I add trip points to the thermal zone?

---

### Post by mhousel on 2009-12-29
> **tw33 said:**
> It is a Toshiba Satellite Pro L300D-11L.
From the log line:
acpi device:04: registered as cooling_device3
Surely there must be some way I can control it?
How can I add trip points to the thermal zone?

I have similar questions...

Where does ACPI get the information for "registering" this "device" and the name cooling_device3.

I have different details but see the same sorts of things and can find no way to set realistic trip points.

Also, just where do these trip points get set?

I wonder who really understands how this stuff works in real detail?

---

### Post by derekmbarnes on 2009-12-31
I've been having similar problems with my Toshiba Satellite M500 -- and so has everyone else with this model. Have a gander at these ACPI trip points:

```
critical (S5):           108 C
passive:                 101 C: tc1=30 tc2=30 tsp=50 devices=CPU0 CPU1 
active[0]:               95 C: devices=FAN0 
active[1]:               85 C: devices=FAN1 
active[2]:               75 C: devices=FAN2 
active[3]:               65 C: devices=FAN3 
active[4]:               50 C: devices=FAN4
```

So the fan in my computer doesn't cool off the processor unless it's 95 C or above (it's at 85 C now and has been steadily climbing). These trip points can no longer be overriden - article on the issue here: [http://lwn.net/Articles/244595/](http://lwn.net/Articles/244595/)

I'll be keeping an eye on this thread for solutions.

---

### Post by tw33 on 2010-01-17
Here is some of the code from my dsdt table. It would be nice if I could use the _ON and _OFF Methods (does anyone know how to call them). Otherwise, maybe changing the first line to One might make the default state On?

    Name (F1ST, Zero)
    Scope (_TZ)
    {
        PowerResource (PFA1, 0x00, 0x0000)
        {
            Method (_STA, 0, NotSerialized)
            {
                Return (F1ST)
            }

            Method (_ON, 0, NotSerialized)
            {
                Store (One, F1ST)
            }

            Method (_OFF, 0, NotSerialized)
            {
                Store (Zero, F1ST)
            }
        }

---

