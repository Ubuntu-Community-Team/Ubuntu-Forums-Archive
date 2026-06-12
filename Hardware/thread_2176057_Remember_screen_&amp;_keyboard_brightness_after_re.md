---
title: "Remember screen &amp; keyboard brightness after reboot"
date: 2013-09-22
forum: Hardware
---

### Post by Amon_Re on 2013-09-22
Hi all,

Not sure if this is the proper forum of this question as it's not really a hardware issue I think. On my new laptop with Ubuntu 13.04 I've noticed that after every reboot Ubuntu forgets the screen brightness level & the keyboard illumination setting.
I've looked around and I've noticed other people having similar issue's and there's a script to do that startup, and it works until I actually log in.

It seems that at login in Ubuntu something resets the settings again to maximum brightness but I can't figure out what.

Any idea's?

---

### Post by Toz on 2013-09-22
Try referencing your script through lightdm's config file. See [https://wiki.ubuntu.com/LightDM#Autorun_a_Command]("https://wiki.ubuntu.com/LightDM#Autorun_a_Command").

I'd try either the "setup-display-script" or the "greeter-setup-script" parameter.

---

### Post by Amon_Re on 2013-09-22
> **Toz said:**
> Try referencing your script through lightdm's config file. See [https://wiki.ubuntu.com/LightDM#Autorun_a_Command]("https://wiki.ubuntu.com/LightDM#Autorun_a_Command").

I'd try either the "setup-display-script" or the "greeter-setup-script" parameter.

Do these scripts run as 'root'? Changing the /sys/class items requires elevated permissions.

---

### Post by Toz on 2013-09-22
Yes. Have a look at the doc in /usr/share/doc/lightdm:
```
zless /usr/share/doc/lightdm/lightdm.conf.gz
```

> # display-setup-script = Script to run when starting a greeter session (runs as root)
# greeter-setup-script = Script to run when starting a greeter (runs as root)
# session-setup-script = Script to run when starting a user session (runs as root)
# session-cleanup-script = Script to run when quitting a user session (runs as root)

---

### Post by Amon_Re on 2013-09-22
Well I tried it and no luck, something still resets the brightness to maximum during logging into the thing.

---

### Post by Toz on 2013-09-22
What is the make and model of your laptop? Can you also post back:

1. Your current kernel boot line:
```
cat /proc/cmdline
```

2. Info about your video cards:
```
lspci -k | grep -A3 VGA
```

3. Info on your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

---

### Post by Amon_Re on 2013-09-22
The laptop is an ASUS N56VB.

```
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=43348536-5734-4e96-82dd-60f2e026d03d ro quiet splash vt.handoff=7
```

```
lspci -k | grep -A3 VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
	Subsystem: ASUSTeK Computer Inc. Device 1477
	Kernel driver in use: i915
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
```

```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
31
30
100
/sys/class/backlight/intel_backlight
4882
1512
4882
```

I should note that this is an Optimus enabled laptop that might have an influence on the cause but I'm still not convinced it's an actual hardware issue, the scripts on this [page]("http://ubuntuforums.org/showthread.php?t=2163556&p=12740865#post12740865") for instance actually work right up until I get to the Lightdm greeter. The brightness is set properly to the previous value and it's only *after* login that it gets set back to 100%

---

### Post by Toz on 2013-09-22
Can you manually manipulate both interfaces? See which of these commands work:
```
echo 50 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...and:
```
echo 2440 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

Its generally a good idea to try to get only one backlight interface so that there isn't any confusion. You might want to give the **acpi_backlight=vendor** kernel parameter a try to see if it can do that for you. It might also solve your brightness resetting issue.

---

### Post by Amon_Re on 2013-09-22
> **Toz said:**
> Can you manually manipulate both interfaces? See which of these commands work:
```
echo 50 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
...and:
```
echo 2440 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

You're right, these both manipulate the screen brightness, I'm assuming the cause is the optimus setup that combines an Intel gfx chip with the NVidia one. 

> Its generally a good idea to try to get only one backlight interface so that there isn't any confusion. You might want to give the **acpi_backlight=vendor** kernel parameter a try to see if it can do that for you. It might also solve your brightness resetting issue.

I can do this by changing ```
GRUB_CMDLINE_LINUX=""
``` to ```
GRUB_CMDLINE_LINUX="]acpi_backlight=vendor"
``` in /etc/default/grub & then running grub-install Correct?

---

### Post by Toz on 2013-09-22
Just one small typo:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```
...but yes. The command is also:
```
sudo update-grub
```

---

### Post by Amon_Re on 2013-09-23
After setting that kernel parameter I was unable to dim the screen and the fan started whirling like mad.

---

### Post by Toz on 2013-09-23
> **Amon_Re said:**
> After setting that kernel parameter I was unable to dim the screen and the fan started whirling like mad.

Its odd that that parameter would make your fan go wild. In that case, you should remove it.
Have you installed bumblebee to manage the optimus graphics? More information [here]("https://help.ubuntu.com/community/HybridGraphics#NVIDIA_Optimus") and [here]("http://followthegeeks.com/a-noobs-guide-to-installing-nvidia-optimus-driver-in-ubuntu/").

---

### Post by Amon_Re on 2013-09-24
> **Toz said:**
> Its odd that that parameter would make your fan go wild. In that case, you should remove it.
Have you installed bumblebee to manage the optimus graphics? More information [here]("https://help.ubuntu.com/community/HybridGraphics#NVIDIA_Optimus") and [here]("http://followthegeeks.com/a-noobs-guide-to-installing-nvidia-optimus-driver-in-ubuntu/").

Yes, I did install Bumblebee and it's working, I can use OpenCL with Darktable without any issue. The screen (and keyboard) brightness is the only thing I can't figure out. I can change the brightness in Settings and it works. I can change brightness with the keyboard shortcuts and it works. I reboot and it's back to 100% *sigh*

If I could manipulate /sys/classes with a non privileged account it wouldn't be an issue at all but for now I'm stumped. It's like something during the log in runs and resets the brightness levels but I have no idea what (or where it stores the settings it uses).

---

