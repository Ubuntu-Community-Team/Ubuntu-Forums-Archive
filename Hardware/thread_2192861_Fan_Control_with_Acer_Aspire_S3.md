---
title: "Fan Control with Acer Aspire S3"
date: 2013-12-10
forum: Hardware
---

### Post by jmahoney1272 on 2013-12-10
Hi,

I have Ubuntu 13.10 installed on my Acer Aspire S3 laptop. Apart from the brightness function keys not working initially (which I have now resolved), I have a problem with the fan running virtually constantly, making my laptop rather noisy. I had a similar problem when running Windows (although the problem was not quite as severe) but managed to resolve it by running a small app that someone had shared on a forum.

I've tried following multiple threads on here and other websites, using fancontrol, but I also get held up by the same problem when trying to use pwmconfig - "There are no pwm-capable sensor modules installed."

Does anyone have any suggestions on how to control the fan speed? I've been monitoring the cpu load and temperatures and they're both reasonably low, so there should be no reason for the fan being on full all of the time.


Thanks.

---

### Post by Toz on 2013-12-10
Hello and welcome to the forums.

Have you tried the acerhdf kernel module to control the fan? See: [http://ubuntuforums.org/showthread.php?t=1998011]("http://ubuntuforums.org/showthread.php?t=1998011").

Or possibly a bios update?

---

### Post by jmahoney1272 on 2013-12-10
Thanks for your reply and for the welcome!

I have already updated the bios, it was my first step when trying to solve this fan issue - no major improvement, unfortunately.

I have tried the acerhdf module, and get the following error message logged: "unknown (unsupported) BIOS version Acer/Aspire S3-391/V2.17".

---

### Post by Toz on 2013-12-10
> **jmahoney1272 said:**
> I have tried the acerhdf module, and get the following error message logged: "unknown (unsupported) BIOS version Acer/Aspire S3-391/V2.17".
Just looking through the [source code]("http://www.piie.net/files/acerhdf_kmod-0.5.30b-linux-3.8.tar.gz") and yes, your system is not supported. There is a way to bypass the bios check and test the module, but before we think about doing that (always risky), what kernel parameters are you currently booting with:
```
cat /proc/cmdline
```
...and would it be possible to get a look at your dmesg log file?
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

EDIT: And there is also this, [acers3fand]("http://sourceforge.net/projects/acers3fand/"), a set of scripts to control the S3 fan. From the website:
> acers3fand is a script which controls your Acer Aspire S3 Ultrabook
fan speed by cpu temperature. It is designed to work with Intel Core i5 CPU
but might work with other cpus as well.

---

### Post by jmahoney1272 on 2013-12-10
My current kernel parameters are:

BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=4ad42862-aaa7-4720-a8c2-7e12d4a10070 ro quiet splash acpi_osi=Linux vt.handoff=7

Dmesg: [http://paste.ubuntu.com/6551386/](http://paste.ubuntu.com/6551386/)

I've just tried acers3fand and it doesn't support the bios version either, unfortunately.

---

### Post by Toz on 2013-12-10
> **jmahoney1272 said:**
> Dmesg: [http://paste.ubuntu.com/6551386/](http://paste.ubuntu.com/6551386/)
Some interesting acpi errors there. Are you having any difficulties with power adapter/battery recognition?
Does your system come with just one video card or does it have some sort of switchable/discreet combination? This command should help:
```
lspci -k | grep -iA2 VGA
```

> My current kernel parameters are:

BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=4ad42862-aaa7-4720-a8c2-7e12d4a10070 ro quiet splash acpi_osi=Linux vt.handoff=7
Your dmesg log file shows that you are also using acpi_backlight=vendor. I'll assume its active. 
Out of curiosity, can you try the **acpi_osi="!Windows 2012"** kernel parameter? This one is a little tricky to setup properly. The relevant lines in your /etc/default/grub file should look like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet rw"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\" acpi_backlight=vendor"
```
...and remember to run "sudo update-grub" to commit the changes. On reboot, post back your dmesg file again and check whether there is any difference with fan management. Also double-check your backlight controls.

> I've just tried acers3fand and it doesn't support the bios version either, unfortunately.
You might want to consider contacting the developer to see if they can add support for your bios version.

---

### Post by jmahoney1272 on 2013-12-10
> **Toz said:**
> Some interesting acpi errors there. Are you having any difficulties with power adapter/battery recognition?
No, I don't seem to be having any obvious issues with either.


> **Toz said:**
> Does your system come with just one video card or does it have some sort of switchable/discreet combination?
Just the one video card:
"VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)    Subsystem: Acer Incorporated [ALI] Device 073a
    Kernel driver in use: i915"


> **Toz said:**
> On reboot, post back your dmesg file again and check whether there is any difference with fan management. Also double-check your backlight controls.

[http://paste.ubuntu.com/6551574/](http://paste.ubuntu.com/6551574/)

Also, my backlight FN keys are still working fine. 

> **Toz said:**
> You might want to consider contacting the developer to see if they can add support for your bios version.

Just posted a message to them, will let you know if I get a response.

---

### Post by Toz on 2013-12-10
Any difference with fan speed using the acpi_osi="!Windows 2012" kernel parameter?

---

### Post by jmahoney1272 on 2013-12-10
It's still running constantly, the fan speed may have reduced a little, still relatively noisy though.

---

