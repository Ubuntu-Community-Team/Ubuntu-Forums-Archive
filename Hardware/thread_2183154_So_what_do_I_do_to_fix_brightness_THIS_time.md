---
title: "So what do I do to fix brightness THIS time?"
date: 2013-10-23
forum: Hardware
---

### Post by shane-animail on 2013-10-23
As long as I have had my current laptop (and the one before it), brightness control has never worked out of the box, neither via hardware keys or the brightness control in system settings.
To force it to work I have to enter various commands to my grub entries.

The thing is, for the last 4 releases on this computer alone, I have had to spend time after installing searching for the command this time around.
What finally gets it working in one release doesn't work in the next.
Why is it so much hassle?

In 13.04 it was this: ```
acpi_backlight=vendor acer_wmi.blacklist=yes
```
Doesn't work in 13.10 and just causes the screen to flash.

---

### Post by Toz on 2013-10-23
What is the make and model of your laptop?

What video card(s) does it have:
```
lspci -k | grep -iA3 VGA
```

What do you currently have as kernel parameters:
```
cat /proc/cmdline
```

What backlight interfaces are being recognized and enabled:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

And finally, what does your Xorg log file say:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

BTW, just noticed it was your first post - welcome to the forums.

---

### Post by shane-animail on 2013-10-24
Thanks for the response but I got it working (kind of) after some experimenting.
Using the following parameters worked this time ```
acpi_backlight=vendor  acpi_osi=Linux
```
This was the combination used for 12.10, if I remember correctly.

I say kind of because although I can now change the brightness, the screen flashes and flickers horrendously with every step.
It's very disappointing that so many computers seem to have this issue with no proper solution in sight.

I have been using ubuntu on and off since hoary hedgehog and it seem the list of manual fixes is getting longer and longer  and I just don't think I can be bothered anymore.

---

### Post by Toz on 2013-10-24
> **shane-animail said:**
> I say kind of because although I can now change the brightness, the screen flashes and flickers horrendously with every step.
It's very disappointing that so many computers seem to have this issue with no proper solution in sight.
If you can post the results to the commands from my post #2, I might be able to get the flickering fixed for you. No promises, but I can try. There were some changes made to the kernel that ships with 13.10 with respect to backlight management (especially for intel graphics chips).

---

### Post by shane-animail on 2013-10-24
Ok, here goes...

```
$ lspci -k | grep -iA3 VGA00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 0487
    Kernel driver in use: i915
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
```
```
$ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz root=UUID=b7803d0b-c9d2-4f9e-a878-f2fb92bc6ef7 ro acpi_backlight=vendor  acpi_osi=Linux quiet splash vt.handoff=7
```
```
$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acer-wmi
9
9
15
/sys/class/backlight/intel_backlight
976
976
976
```
And finally the pastebinit link: 
[http://paste.ubuntu.com/6297180/](http://paste.ubuntu.com/6297180/)

---

### Post by Toz on 2013-10-24
Try this:
1. With root privledges, create the file /usr/share/X11/xorg.conf.d/20-intel.conf:
```
sudo -i gedit /usr/share/X11/xorg.conf.d/20-intel.conf
```
...enter your password when promtped.

2. Copy/paste this into the new window:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```

3. Save the file.

4. Log out and back in again and test.

If it still doesn't work, remove the **acpi_backlight=vendor** kernel parameter and try again.

---

### Post by shane-animail on 2013-10-25
With all the parameters removed, adding the intel conf file does make brightness controls work.
It is a little different to the previous fixes in that it has a lot more "steps" to the control (previously I could go from fully dim to fully bright in about 5 steps, now it's about 20).
However, the flickering is only partially fixed.  No flickering when turning brightness up, but still flickers badly when dimming.

In the past I used to love all this fiddling around and fixing things but I have grown to hate it of late and would rather things just worked but still, many thanks for taking the time out to help.

---

