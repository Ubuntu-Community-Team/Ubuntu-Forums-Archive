---
title: "Immediate return from suspend / hibernate"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by private_lock on 2007-07-24
Hello!

Whenever I send my Laptop to sleep, it blanks out the screen for some seconds and returns almost instantly with the screensaver on.

In /var/log/messages I found the attached log for suspend2disk and suspend2ram

My hardware is:
Samsung R40+ Aura T2080 Deron
Intel Pentium Core Duo
ATI graphics with flgrx drivers
2 GB RAM
2 GB SWAP
the rest of the harddrive is "/" in a single partition

Software:
Kubuntu Feisty Fawn 7.04

Can you please help me, to get this streight?

private_lock

PS: I'd also be greatful for Howtos and background-reading. For example this one was very instructive: [http://www.caiacoa.de/wiki/index.php/Samsung_R40-T2050_Chasubi](http://www.caiacoa.de/wiki/index.php/Samsung_R40-T2050_Chasubi) (But unfortunately that is a slightly different hardwareconfiguration. At least it states, that s2d and s2r worked out-of-the-box)

---

### Post by zanglang on 2007-07-24
I think your swap partition didn't have enough space to fit all of your RAM during hibernation. You'll have to make sure that the free swap is always big enough to fit the entirety of your used memory when you do so. If your programs swap a lot maybe consider boosting it to something like 1.1-1.5x your current size?

---

### Post by private_lock on 2007-07-24
Actually I don't think this to be a memory issue ... I closed all programs for the first test of hibernation for not loosing any data. Or would it try to save unused empty RAM to disk?

Anyway ... how would I convert some harddrive sectors from being "/" to become swap? I've already spent a week, to get my system running and productive ... I don't want to start all over again.

---

### Post by zanglang on 2007-07-24
Ah, you're probably correct. I've once got these symptoms when my swap was corrupted, and since there wasn't any swap to hibernate to it just went into screensaver mode. But looking at your messages file yours just might be a hardware problem, these look suspicious:
> Jul 24 11:45:27 samson kernel: [15209.392000] ACPI: PCI interrupt for device 0000:02:09.1 disabled
Jul 24 11:45:27 samson kernel: [15210.392000] [fglrx] firegl_gps_setpowerdown .
Jul 24 11:45:27 samson kernel: [15210.392000] [fglrx] firegl_gps_setpowerup .
Jul 24 11:45:27 samson kernel: [15210.424000] ACPI: PCI Interrupt 0000:02:09.1[C] -> GSI 22 (level, low) -> IRQ 17
Jul 24 11:45:27 samson kernel: [15210.432000] pnp: Device 00:06 does not support activation.
Jul 24 11:45:27 samson kernel: [15210.432000] pnp: Device 00:07 does not support activation.
Jul 24 11:45:27 samson kernel: [15211.052000] Some devices failed to suspend
I don't own an ATI card so I can't comment... have you checked if anyone else with the driver experience this problem?

---

### Post by private_lock on 2007-07-24
I tried to modify /etc/default/acpi-support as adviced here:

[http://ubuntuforums.org/showthread.php?t=428229&highlight=hibernate+fglrx](http://ubuntuforums.org/showthread.php?t=428229&highlight=hibernate+fglrx)

This had no effect at all

Then I tried to use uswsusp as adviced here:

[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

At first it did not recognize my system and the --force option just crashed and I had to reboot.

Finally I searched for and did not find /etc/acpi/hibernate.sh as indicated here:

[http://ubuntuforums.org/showthread.php?t=459956&highlight=hibernate+fglrx](http://ubuntuforums.org/showthread.php?t=459956&highlight=hibernate+fglrx)

To sum it up:
My Problem is, I don't even achieve the suspend state. Those topics relate to problems with waking up like no fan, no keyboard, no screen ... This might be an issue, once I manage to knock my laptop out.

Any more ideas? Are there are more advanced options available for the uswsusp s2ram

---

### Post by nick_h on 2007-07-25
This [HowTo](http://ubuntuforums.org/showthread.php?t=505890) is worth reading.

You could also try suspend from a console using /etc/acpi/sleep.sh

I think s2ram is mainly useful when the display does not resume.  A good article can be found [here](http://en.opensuse.org/S2ram).

---

### Post by private_lock on 2007-07-25
According to this [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI) I've collected some additional infos in the attachement. But the /var/log/kern.log.0 is to large, to attach it here.

@nick

Calling /etc/acpi/sleep.sh will blank my screen and leave no other possibility, than to reboot the machine.

I'll work through the other links over the weekend

Thanks
private_lock

---

### Post by private_lock on 2007-07-26
OK, this morning I did this tutorial:

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

```
sync; echo 1 > /sys/power/pm_trace; /etc/acpi/sleep.sh force
```

The screen went black for some seconds and I was back ... no screensaver and now password needed...

In dmesg output I found:
```

[    3.334692] ACPI: (supports S0 S3 S4 S5)
[    3.334741]   Magic number: 15:313:267
[    3.334744]   hash matches device eisa.0
[    3.334776]   hash matches device ttyx9
[    3.334791]   hash matches device ttyuc

```

But how do I read this?

They say
> 
There may well be another 'hash matches' line beyond that. If so, then you are in luck because the last one is the likely culprit. For example:

hash matches device i2c-9191 

The only way to prove this is to remove the module prior to initiating suspend. Repeat as needed... 


Does this mean anything to one of you?

private_lock

---

### Post by private_lock on 2007-07-26
Carefully re-reading the dmesg output from my last post I found this:

[code]
[ 5665.256000] fglrx_pci 0000:01:05.0: suspend
[ 5666.236000] [fglrx] firegl_gps_setpowerdown .
[ 5666.236000] [fglrx:MCIL_AllocateMemory] *ERROR* MCIL_AllocateMemory system memory failed.
[ 5666.236000] [fglrx:firegl_gps_SetPowerState] *ERROR* Gps set power down failed.
[ 5666.236000] [fglrx] firegl_gps_setpowerup .
[ 5666.252000] pci_device_suspend(): fglrx_pci_suspend+0x0/0xc0 [fglrx]() returns -5
[ 5666.252000] suspend_device(): pci_device_suspend+0x0/0x60() returns -5
[ 5666.252000] Could not suspend device 0000:01:05.0: error -5
[ 5666.252000] pci 0000:02:05.0: resuming
[/code

I had to install the xorg-driver-fglrx version 7.1.0-8.34.8+2.6.20.5-16.29 for my ATI Radeon Xpress 1250 because otherwise the Ubuntu-Live-CD would fail to load the X-Server. Moreover, without it I cannot use the 3D-acceleration. lspci reports it as "01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 7942"

It seems, I need to sort this out first. Who is developing the fglrx-drivers? They say "Ubuntu Kernel Team". Where can I search for / file a bug-report?

---

### Post by nick_h on 2007-07-26
You can search for and report bugs at [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Is there an alternative driver you can test with?

The fatal errors at the end of your sleep_sh_force.txt file seem to occur in the /etc/acpi/resume.d/72-acpi-pain.sh script.

---

### Post by private_lock on 2007-07-26
I've filed a bug report now at:
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/128617](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/128617)

I did not test any other driver ... It is just, that the Ubuntu-Live-CD would not run without fglrx ... the X-Server complained, that it could not find a suitable valid video mode / resolution.

---

