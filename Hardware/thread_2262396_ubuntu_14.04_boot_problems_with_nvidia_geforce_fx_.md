---
title: "ubuntu 14.04 boot problems with nvidia geforce fx 5500"
date: 2015-01-24
forum: Hardware
---

### Post by super kim on 2015-01-24
Hello, I am having problems setting up my nvidia card with ubuntu 14.04

processor: Intel® Pentium(R) 4 CPU 2.80GHz × 2 
graphics: GeForce FX 5500/PCI/SSE2
os: 64-bit
kernel: 3.13.0-44-generic
driver: nvidia legacy binary driver version 173.14.39

When I power up the machine I see the geforce bios screen, then the dell bios screen, then there is a '-' on the top left of the screen, which flashes. This is when the computer restarts itself and repeats the process except the last part with the '-'. On the second run I get the boot options, the first option (to boot normally) restarts the computer again, the second option (recovery mode) works, on the next screen I get the option to exit recovery mode and boot normally. If i select this ubuntu will then boot up fine.

I'm lost as to where I should start. Can anyone suggest any boot logs I could look at to try and find out why I can't boot normally, thanks in advance.

---

### Post by mooreted on 2015-01-24
I would try installing a 32-bit OS on that machine, and something lighter like Lubuntu.

---

### Post by oldfred on 2015-01-24
How much RAM?
It if boots I do not think 32bit will help unless you have less than 2GB of RAM.

Log files can be viewed with Log File Viewer or any text editor.
Boot logs would be in /var/log/dmesg
That is long, but you want to look for outright errors, warnings, repeated tries at loading a driver and either later success or failure and very long differences in the timestamps.

---

### Post by super kim on 2015-02-04
I have more than 2GB of RAM.

You are right when you say the log files are long... But I did find some bits in the dmesg that said "Warning":
[    8.446841] systemd-udevd[215]: starting version 204
[    9.588755] intel_rng: Firmware space is locked read-only. If you can't or
[    9.588755] intel_rng: don't want to disable this in firmware setup, and if
[    9.588755] intel_rng: you are certain that your system has a functional
[    9.588755] intel_rng: RNG, try using the 'no_fwh_detect' option.
[    9.644199] systemd-udevd[220]: renamed network interface eth0 to eth2
[    9.744285] ACPI Warning: 0x0000000000000828-0x000000000000082f SystemIO conflicts with Region \GLBC 1 (20131115/utaddress-251)
[    9.744513] ACPI Warning: 0x0000000000000828-0x000000000000082f SystemIO conflicts with Region \SACT 2 (20131115/utaddress-251)
[    9.744731] ACPI Warning: 0x0000000000000828-0x000000000000082f SystemIO conflicts with Region \SSTS 3 (20131115/utaddress-251)
[    9.744948] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.745130] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    9.917409] leds_ss4200: no LED devices found
[   10.109182] [drm] Initialized drm 1.1.0 20060810
[   10.189845] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   10.791459] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   11.434114] snd_hda_intel 0000:00:1b.0: irq 42 for MSI/MSI-X

---

### Post by super kim on 2015-02-04
Also the word "error" appeared here:

[   63.218593] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   64.921682] init: failsafe main process (1066) killed by TERM signal

---

### Post by oldfred on 2015-02-04
I do not know details on any of those warnings, or if a real issue.

I doubt your system is new enough to have a AHCI BIOS setting for hard drive. If you do change it from IDE to AHCI.

Are there any entries with large time stamp delta's? I think the one before the gap is the issue but not sure.

---

