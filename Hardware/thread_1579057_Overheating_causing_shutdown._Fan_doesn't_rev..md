---
title: "Overheating causing shutdown. Fan doesn't rev."
date: 2010-09-21
forum: Hardware
---

### Post by narnie on 2010-09-21
Hello,

I'm having a significant problem on my computer. It will overheat without triggering the higher fan speed setting that I know this fan is capable of using. Previous Ubuntus haven't had this problem, but past several iterations, including Lucid, do.

I have to have my computer using the powersave governor. Example: last night, I had the computer on. I don't think it was doing anything taxing. It was just on overnight. I get up in the morning, and the computer is off. I know it is overheating because that happens before I set the governor. Sys log shows:

```
Sep 21 03:40:00 toshiba-laptop kernel: [41677.029140] CPU1: Temperature above threshold, cpu clock throttled (total events = 1)
Sep 21 03:40:00 toshiba-laptop kernel: [41677.029150] CPU0: Temperature above threshold, cpu clock throttled (total events = 1)
Sep 21 03:40:00 toshiba-laptop kernel: [41677.029175] Disabling lock debugging due to kernel taint
Sep 21 03:40:00 toshiba-laptop kernel: [41677.032787] CPU1: Temperature/speed normal
Sep 21 03:40:00 toshiba-laptop kernel: [41677.032791] CPU0: Temperature/speed normal
Sep 21 03:40:23 toshiba-laptop kernel: [41700.041348] Machine check events logged
Sep 21 09:18:50 toshiba-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
```

It will overheat so quickly, it doesn't even have time to log it, and the BIOS will turn it off.

There are no BIOS settings for the fan.

How could I control the fan speed? I can write a script to do so at certain trigger points, but I don't know how to do the fan.

My trip points and some other info:

```
$ cat /proc/acpi/thermal_zone/THRM/trip_points 
critical (S5):           104 C
passive:                 104 C: tc1=2 tc2=5 tsp=300 devices=CPU0 CPU1 
active[0]:               70 C: devices= FAN
```

```
$ cat /proc/acpi/fan/FAN/state 
status:                  on
```

I could really use the help of a hardware guru. As long as I know how to speed up the fan and return it to normal (or auto), I can write the script needed.

If needed, I have a Toshiba A505-S6965. I know Toshiba's are notorious for overheating and fan probs :(

Thanks,
Narnie

---

### Post by arvevans on 2010-09-21
This is going to be tricky if you cannot keep it up long enough to log in.

There are a number of utility software programs specifically for the Toshiba and it's various hardware items.  These include:
[INDENT]"toshset"   Access to much of the Toshiba laptop hardware interface
"toshutils"   Toshiba laptop utilities
"fnfxd"    ACPI and hotkey daemon for Toshiba laptops
"aes2501-wy"    Userspace software for 2501 fingerprint scanner
"acpitool"    Command line ACPI toolkit
"acpi-support"    Scripts for handling many ACPI actions
"acpitool-dbg"    Command line debugging tool for ACPI
[/INDENT]

Logging in using just the command line interface may be faster and give the computer less time to overheat.  If you can do this then you might be able to successfully perform "apt-get install xxxxx" for those Toshiba ACPI utilities that are needed to run your fan and other ACPI controlled hardware.

---

### Post by narnie on 2010-09-21
> **arvevans said:**
> This is going to be tricky if you cannot keep it up long enough to log in.

No, it is not that bad. As you probably know, the governor is set to performance at boot. /etc/init.d/ondemand changes it to just that, ondemand 1 min after boot. I have a script that I wrote that automatically changes it to powersave at 2 mins (just haven't gotten around to modifying the /etc/init.d/ondemand script to do this myself). cpufreq has been my friend. When I need performance, I can power it up and just watch the temp. I have scripts I can run with a quick alt-F2 that take care of it for me. Mostly, have to watch playing video (watching transformers G1 with my son and youtube, esp).

> There are a number of utility software programs specifically for the Toshiba and it's various hardware items.  These include:

My understanding for the toshiba tools is that they won't work on these newer Toshibas. I have installed some before to no avail and modprobed them and they gripe about not finding the chipsets (if memory serves).


I will go through the tools that you gave though to double check. Thanks for them. Perhaps I'll find what I need after all.

Any help on how to use the proc dir or sys dir to increase the fan speed would be excellent.

Gratefully,
Narnie

---

### Post by narnie on 2010-09-21
Nope, just tried again. Can't use them.

```
sudo toshset -fan 3
required kernel toshiba support not enabled.
```

```
sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.32-24-generic/kernel/drivers/platform/x86/toshiba_acpi.ko): No such device
```

This laptop uses the INSYDE bios. Not a toshiba or even phoenix bios.

---

### Post by steve161 on 2010-09-21
I have the same bios, and what worked for me was to add either acpi_osi=Linux or acpi_osi=\\\"Linux\\\" to etc/default/grub.  The line you need to change should look like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

Try both parameters.  Run sudo update-grub after every change, and reboot.  Just browsing the web and my core temp is showing 45C

---

### Post by narnie on 2010-09-21
> **steve161 said:**
> I have the same bios, and what worked for me was to add either acpi_osi=Linux or acpi_osi=\\\"Linux\\\" to etc/default/grub.  The line you need to change should look like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

Try both parameters.  Run sudo update-grub after every change, and reboot.  Just browsing the web and my core temp is showing 45C

Tried both to no avail to both of those.

I tried dling, compiling, and installing the omnibook module that is supposed to work for this BIOS. No avail on the fan for me. Info on this module can be found at [https://sourceforge.net/apps/mediawiki/omnibook/index.php?title=Main_Page]("https://sourceforge.net/apps/mediawiki/omnibook/index.php?title=Main_Page")

I have submitted a bug report on [https://sourceforge.net/tracker/index.php?func=detail&aid=3073003&group_id=174260&atid=868542]("https://sourceforge.net/tracker/index.php?func=detail&aid=3073003&group_id=174260&atid=868542")

I appreciate all the suggestions and ask they keep coming. One is bound to work (trying to be optimistic, here).

Cheerio,
Narnie

---

