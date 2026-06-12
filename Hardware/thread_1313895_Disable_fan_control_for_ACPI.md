---
title: "Disable fan control for ACPI"
date: 2009-11-04
forum: Hardware
---

### Post by Ader_ on 2009-11-04
Hi!
the BIOS on my laptop is faulty in such a way that ACPI does not seem to be able to turn the fan on, only off. This leads to the computer overheating. If I turn ACPI=off the fan is on all the time which is fine by me. Is there a way of configuring ACPI so that it leaves fan control alone while keeping on doing all the other things it does?

Rasmus

---

### Post by tw33 on 2009-12-10
*bump*
This is a good question. acpi=off is the only way I could the fan to behave on my Toshiba Satellite Pro L300D-11l. This means I can't suspend or control the volume :(

Since ubuntu is unable to control the fan, how can I disable it from trying without disabling everything else?

---

### Post by cyberey66 on 2009-12-10
Search for a repaired "DSDT table" for your laptop.   If you find it, you can make the kernel use the corrected table and all your ACPI stuff will work.  I had to do that with my netbook

---

### Post by Ader_ on 2010-01-11
Hi all!
On my Fujitsu Siemens Amilo L1310G I was able to do miracles by adding acpi.power_nocheck=1 to the grub:

```
sudo gedit /etc/default/grub
```

Add

```
acpi.power_nocheck=1
```

To the end of the line that looks something like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

It should now look something like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi.power_nocheck=1"
```

Save and close and then do:

```
sudo update-grub
```

After I restart, fan control is working as it has never before. I hope this can be of use to some of you!

Rasmus

---

### Post by Takala on 2010-04-11
> **Ader_ said:**
> Hi all!
On my Fujitsu Siemens Amilo L1310G I was able to do miracles by adding acpi.power_nocheck=1 to the grub:

```
sudo gedit /etc/default/grub
```Add

```
acpi.power_nocheck=1
```To the end of the line that looks something like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```It should now look something like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi.power_nocheck=1"
```Save and close and then do:

```
sudo update-grub
```After I restart, fan control is working as it has never before. I hope this can be of use to some of you!

Rasmus

I confirm! I have the same machine and it works on ubuntu 9.10. Thank you!

---

### Post by carlossl on 2010-04-14
Hi! I just wanted to tell you that I found an update for my BIOS, it was release recenlty in the Toshiba website, so you could give it a try (just be careful). I found this post because I had a similar problem with my Toshiba Satellite L305D-SP6805R, which also had a buggy BIOS...

I knew it was buggy because had two problems: 

1. I have an AMD Athlon X2 64bit processor. When I tried to install Windows 7 64-bits, a blue screen appeared when loading the installation CD, so I tried with Linux...

2. When I tried to install any Linux distro (I tried with Ubuntu, Fedora, ArchLinux, openSUSE, many versions of them) with all of them my computer would shut off before I could install the OS. Sometimes I would have time to quickly download the sensors package (sudo apt-get install lm_sensors | sudo pacman -S lm_sensors, depending on the distro) and see the temperature for my processor. It was always between 90ºC and 100ºC, being 105ºC the max limit with which the computer would shut off.

I had to go back with Windows 7 32 bits and from there install the BIOS update, so I could switch to Windows 7 64 bits. But when I tried with a Linux, I would still have the same problem, UNLESS I left the Live CD welcome screen for 10 seconds, and only then I could get the fan to work and install Linux. When I restarted, I had to do the same in the grub screen, leave it for 10 seconds and just then the fan would turn on, and would stay on all the time.

Anyway, I wanted to share my experience in case it works for someone.

Funny, you posted 6 months ago, and since then, I haven't found a good solution. Hope yours works, adding the acpi line to grub.

---

### Post by carlossl on 2010-04-15
So... I installed last night Ubuntu 10.04 64 bits, and I can say that it works better than Windows 7 64 bits (the important thing here is that I updated the BIOS).

Windows kept the processor temperature at 70-80ºC, while Lucid keeps it at 40-50ºC !!!
Isn't that amazing? I never thought any Linux distro would manage my computer better than Windows, ever.

My laptop is a Toshiba Satellite L305D-SP6805R.
- Processor: AMD Athlon X2 64 bits
- Wireless: Atheros AR5001 (worked from the beginning)
- Video: ATI Radeon HD 3100 (worked from the beginning, even without the restricted driver)
- BIOS: Insyde H2O, version 1.8 (recently updated, fixed all my problems, got the update from Toshiba website, looking for the SP6805 models' BIOS)

---

