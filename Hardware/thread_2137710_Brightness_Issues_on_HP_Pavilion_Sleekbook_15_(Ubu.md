---
title: "Brightness Issues on HP Pavilion Sleekbook 15 (Ubuntu 13.04, 64 bit)"
date: 2013-04-21
forum: Hardware
---

### Post by Marzian on 2013-04-21
Hello,
By controlling the display brightness with the hotkeys (F2), when I reach the minimum, the screen turns black, and the lowest "step" I can reach is still too bright for the evening. How can I prevent it? 

The only previous discussion I could fine is this one ([http://askubuntu.com/questions/191211/minimum-brightness-setting-causes-black-screen](http://askubuntu.com/questions/191211/minimum-brightness-setting-causes-black-screen)) but it was refering to 12.04, another model of HP and they just suggested filling a bug report. Is this the case this time too?

Thank you!

---

### Post by Marzian on 2013-04-22
Using the command cat /sys/class/backlight/acpi_video0/brightness I found out that the minimum brightness value is 10. Starting from 9, it goes black. Can I solve this? And - if not - could I at least set my hotkeys so that F2 doesn't go below 10?

---

### Post by Marzian on 2013-04-23
Another issue with brightness, but I'm posting here because they could be related: after reboot, the brightness of the previous session is not saved, and I have already tried the solution here:

[http://megatechtoday.blogspot.it/2012/08/save-screen-brightness-of-laptop-in.html](http://megatechtoday.blogspot.it/2012/08/save-screen-brightness-of-laptop-in.html)

---

### Post by Toz on 2013-04-23
Have you tried the **acpi_backlight=vendor** kernel boot parameter? See the Kernel Boot Parameters link un my signature for more information on how to temporarily test it.

Otherwise, some more information would be helpful. Open a terminal window, type in the following commands, and post back the results:
```
lspci | grep VGA
cat /proc/cmdline
```

---

### Post by Marzian on 2013-04-24
I tried the parameter. The backlight settings seems now to be saved after a reboot, but no changes in the dark sceen below the "10" value.

Here the results of the commands:

```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
```

```
$ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.8.8-030808-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
```

Thanks

---

### Post by Toz on 2013-04-24
Can you try the following combinations of kernel parameters to see if any will work:
```
acpi_osi=Linux acpi_backlight=vendor
```
```
acpi_osi=
```
```
acpi_osi=\"!Windows 2012\"
```

Also, can you post back the contents of your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by Marzian on 2013-04-24
Tried 'em all: no difference.

Here the log: [http://paste.ubuntu.com/5599059/](http://paste.ubuntu.com/5599059/)

---

### Post by Toz on 2013-04-24
From your log file:
> [   12.115406] ACPI Error: Too many duplicates in _BCL package

From the acpi source:
> "ACPI method _BCL (Query List of Brightness Control Levels Supported) contains too many duplicated brightness levels in the returned package and this is non-standard."

Is there possibly a bios update available?

I'd be interested in seeing if there are any changes to this log file (and this message) if you boot with **acpi_osi=\"!Windows 2012\"** and **acpi_backlight=vendor** (separately). Perhaps you could try these kernel boot parameters again and post back /var/log/dmesg while booted with each of those parameters.

Otherwise, you may need to create a bug report.

Note: to boot with the acpi_osi=\"!Windows 2012\" parameter, the GRUB_CMDLINE_LINUX line in /etc/default/grub should look like this:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

---

### Post by Marzian on 2013-04-25
The log I posted was from setting GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\"".

While, with GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor", this is the result ([http://paste.ubuntu.com/5600481/](http://paste.ubuntu.com/5600481/)) and as far as I can see that ACPI error still pops up. I suppose I'll just live with it and compile a bug report.

But... Since you looked at the log, could I please ask if by any chance you noticed anything wrong also with the wireless? I'm having problems with that one too ([http://ubuntuforums.org/showthread.php?t=2137576](http://ubuntuforums.org/showthread.php?t=2137576)).

(I chose an HP thinking it would be easily compatibile with Linux... Doesn't seem to be the case)

---

### Post by Toz on 2013-04-25
> **Marzian said:**
> The log I posted was from setting GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\"".
I don't think so. From your log file:
```
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.8.8-030808-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
```
Can you try it again? Also post back the results of:
```
cat /proc/cmdline
```

> While, with GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor", this is the result ([http://paste.ubuntu.com/5600481/](http://paste.ubuntu.com/5600481/)) and as far as I can see that ACPI error still pops up. I suppose I'll just live with it and compile a bug report.
I'm still not seeing that in your command line:
```
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.8.8-030808-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
```
What process are you using to test the kernel boot parameter? Are you editing /etc/default/grub? Are you running "sudo update-grub" to commit the change?

> But... Since you looked at the log, could I please ask if by any chance you noticed anything wrong also with the wireless? I'm having problems with that one too ([http://ubuntuforums.org/showthread.php?t=2137576](http://ubuntuforums.org/showthread.php?t=2137576)).
I'm not a networking specialist, but have a read through this thread: [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/221247]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/221247"). Otherwise, try PM'ing chili555 and politely asking him to have a look at that thread.

> (I chose an HP thinking it would be easily compatibile with Linux... Doesn't seem to be the case)
Newer hardware sometimes takes time before all the bugs are worked out and its properly supported. I have an HP Folio 9470m and also have one remainging nagging bug with the sound system that I'm waiting for a fix for. Seems to be the nature of the beast.

---

### Post by Marzian on 2013-05-29
I'm very very sorry... I was editing /etc/default/grub but not giving "sudo update-grub"!

acpi_backlight=vendor turned out to be enough.

Thanks again.

---

