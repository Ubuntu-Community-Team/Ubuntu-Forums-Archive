---
title: "Linux boot hangs on ACPI message"
date: 2010-01-18
forum: Hardware
---

### Post by Tibuda on 2010-01-18
I have a laptop that came with an [Ubuntu-derivative]("http://www.oneos.info/") pre-installed. The laptop is 100% compatible with Ubuntu, all the LiveCDs since Gutsy worked out-of-the-box. Except for the last week, that the installed Karmic stopped to boot. I have tried to boot all the LiveCDs I have (gutsy 32bit, hardy 32bit, intrepid 32bit, jaunty 64bit and karmic 64bit), but none have worked. When I tried to boot from GRUB recovery mode, it displays a lot of messages and starts to hang. The last message is:
```
ACPI: Core revision 20090320
```
I did some research on ACPI, and found that I could disable ACPI but adding the following to the GRUB boot:
```
acpi=off noapic nolapic
```
After adding this argument, the boot now hangs with the following message and then the screens gets scrambled:
```
Boot video device
```

I have tried to boot another distro too, but it have the same behaviour. Then I tried the Windows XP installer I have, and it worked fine. This is not what I want, as I don't have a license for this laptop, and I don't really need it.

After installing XP, I have also tried to use Linux with Wubi, but it didn't worked too.

Any ideas on how to fix it?

Thanks

---

### Post by Tibuda on 2010-01-20
bump

Linux works fine on VirtualBox. I think something is wrong with my hardware.

---

### Post by Tibuda on 2010-01-25
bump :(

I'll buy Windows 7, but I still wish to install Linux again in this laptop.

---

### Post by Tibuda on 2010-01-28
bump

---

### Post by drdanielfc on 2010-01-28
What do the live disks do when you're trying to boot off of them?

---

### Post by Tibuda on 2010-01-29
> **drdanielfc said:**
> What do the live disks do when you're trying to boot off of them?

Thanks for the reply.

The Live CDs did the same as the normal boot, but yesterday the computer shop guy have already fixed it. It looks like I have enabled an option in the BIOS incompatible with Linux. I'll mark this as solved.

---

### Post by skralljt on 2010-02-24
whatever that setting was, it would be helpful if you would elaborate so that others who came here with the same problem (like myself) can fix it.  All I did was change processors.  They were both amd 939 but with two different linux distros I hang at acpi: core revision xxxxxxxx.  Going to try booting with acpi=off.

---

### Post by skralljt on 2010-02-24
> **skralljt said:**
> whatever that setting was, it would be helpful if you would elaborate so that others who came here with the same problem (like myself) can fix it.  All I did was change processors.  They were both amd 939 but with two different linux distros I hang at acpi: core revision xxxxxxxx.  Going to try booting with acpi=off.

After putting "acpi=off nolapic" in /boot/grub/menu.lst after the kernel I was trying to boot, it booted.

---

### Post by Tibuda on 2010-02-24
> **skralljt said:**
> whatever that setting was, it would be helpful if you would elaborate so that others who came here with the same problem (like myself) can fix it.  All I did was change processors.  They were both amd 939 but with two different linux distros I hang at acpi: core revision xxxxxxxx.  Going to try booting with acpi=off.

"acpi=off nolapic" didn't worked for me. I had to disable "Support for Legacy USB devices" in the BIOS.

Good it worked for you.

---

### Post by nicks27 on 2010-03-09
I had the same problem (halting on "ACPI: Core revision 20090521") on a Clevo M66JE laptop.
It's running Xubuntu v9.10 with no system updates applied since the 2.6.31-20 kernel 5 days ago, and was booting fine until today.
I also seem to have resolved this by disabling "USB BIOS Legacy Support" in the BIOS (I didn't need to make any "acpi=off" or similar changes)... booting ok now.

---

### Post by rounder8 on 2013-03-10
I got the exact same problem (halting on "ACPI: Core revision xxxx") on my Lenovo W500.

The fix was to turn on OS switchable graphics detection from BIOS.

---

