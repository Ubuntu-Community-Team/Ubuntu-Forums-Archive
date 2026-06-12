---
title: "ACPI fan off? (fan control)"
date: 2012-07-04
forum: Hardware
---

### Post by pmatos on 2012-07-04
Hello,

I assembled a new PC (P8Z77-I Ivy Bridge motherboard).
I ran sensors detect but the only thing I get with sensors is:
```
pmatos@jupiter:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8°C  (crit = +106.0°C)
temp2:        +29.8°C  (crit = +106.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +38.0°C  (high = +85.0°C, crit = +105.0°C)
Core 0:         +32.0°C  (high = +85.0°C, crit = +105.0°C)
Core 1:         +33.0°C  (high = +85.0°C, crit = +105.0°C)
Core 2:         +25.0°C  (high = +85.0°C, crit = +105.0°C)
Core 3:         +33.0°C  (high = +85.0°C, crit = +105.0°C)
```

Fans are currently running at a very high speed (quite noisy).

I want them to control themselves so that they only turn on when they see fit.

I noticed the following using dmesg:
```
[    0.826817] ACPI: Fan [FAN0] (off)
[    0.826834] ACPI: Fan [FAN1] (off)
[    0.826851] ACPI: Fan [FAN2] (off)
[    0.826867] ACPI: Fan [FAN3] (off)
[    0.826882] ACPI: Fan [FAN4] (off)
```

I am wondering if this is affecting sensors detect ability to see the fans and show their speed (at the same time allowing the kernel to set fan speeds as it sees fit).

Any suggestions?

---

### Post by Redblade20XX on 2012-07-04
Who manufactured your motherboard or the BIOS?

See if they have any documentation on using the board or the BIOS.

You should look into the BIOS to see if there are any fan control options or thermal trip point since the BIOS usually controls these aspects.

-Red

---

### Post by pmatos on 2012-07-05
> **Redblade20XX said:**
> Who manufactured your motherboard or the BIOS?

See if they have any documentation on using the board or the BIOS.

You should look into the BIOS to see if there are any fan control options or thermal trip point since the BIOS usually controls these aspects.

-Red

Thanks Red, I actually thought it was the OS (Ubuntu) that could communicate with the mobo/bios and set up the fan speed according to the temperatures. I will look at my bios and see what I can do.

---

### Post by dino99 on 2012-07-05
Lot of work have been done lately on kernel 3.5 about acpi, so better to install it

---

### Post by pmatos on 2012-07-05
> **dino99 said:**
> Lot of work have been done lately on kernel 3.5 about acpi, so better to install it

Is there any ubuntu 'approved' way to install it? apt-get?
Or it boils down to download/configure/make?

---

### Post by pmatos on 2012-07-05
> **Redblade20XX said:**
> Who manufactured your motherboard or the BIOS?

See if they have any documentation on using the board or the BIOS.

You should look into the BIOS to see if there are any fan control options or thermal trip point since the BIOS usually controls these aspects.

-Red

Btw, the motherboard is an ASUS P8Z77-I and the BIOS seems to be ASUS too. The motherboard has some settings to control fan. However, if I set the settings to silent or even manually, I still get fans at full speed in linux. I wonder if incorrectly linux is overriding these settings...

---

### Post by Redblade20XX on 2012-07-05
> **pmatos said:**
> Btw, the motherboard is an ASUS P8Z77-I and the BIOS seems to be ASUS too. The motherboard has some settings to control fan. However, if I set the settings to silent or even manually, I still get fans at full speed in linux. I wonder if incorrectly linux is overriding these settings...

Do you have the most current BIOS?

Hmm... linux is not suppose to mess with BIOS settings.

Try some of these options to see if the kernel is doing something wrong.
[https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

In your BIOS setting, enable and save the silent option or the manual option, push some of these kernel options and see what happens.

-Red

---

