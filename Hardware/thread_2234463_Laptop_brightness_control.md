---
title: "Laptop brightness control"
date: 2014-07-14
forum: Hardware
---

### Post by MrMe01 on 2014-07-14
***Solved by editing grub, see post 7***

Under both Debian and Windows I get 10 levels of brightness, under 14.04 I get 7. I'm fortunate to have two of the same machine. The difference between them is the lower end. It doesn't seem to go down as low when side by side with the other laptop running Windows 7.


It's a Core i3 370M processor with Ironlake graphics, not sure if it's graphics or power management though.

---

### Post by jeremy31 on 2014-07-15
It might just be different kernel versions between debian and ubuntu especially if both machines have the same BIOS version

---

### Post by MrMe01 on 2014-07-15
What can I do about it? I like using Ubuntu over Debian, but as someone who's regularly running to the low end of the battery, that low screen brightness is somewhat needed.

---

### Post by jeremy31 on 2014-07-15
You can check kernel versions using ```
uname -r
```
Ubuntu 14.04 is likely using 3.13.0-?  I have no idea what your debian would have but a simple code in terminal should lower your brightness depending on some files
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/max_brightness; done
```

Isn't there a slider in system settings or power management that allows more settings?

---

### Post by MrMe01 on 2014-07-15
Here's the output of that command, brightness fully up
/sys/class/backlight/acpi_video0
10
10
/sys/class/backlight/intel_backlight
4598
4882

Fully down,
/sys/class/backlight/acpi_video0
0
10
/sys/class/backlight/intel_backlight
1349
4882

Not sure what how to interpret that though. I don't have Debian installed so I can't tell you what the same command would say.

Kernel version is 3.13.0-30-generic

---

### Post by MrMe01 on 2014-07-15
Okay, after repeating the command at different brightness levels, this is happening.
Using the */10 from the above comment.

Actual screen brightness doesn't change between 6 and 10. On 5 it changes. I'm not sure if 10 is the highest brightness the backlight will go, but I do know that 0 isn't the lowest.

---

### Post by jeremy31 on 2014-07-15
I wonder if editing grub to make it switch to the intel_backlight might help 
```
sudo gedit /etc/default/grub
``` 
and make the line that usually looks like this ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
be this instead ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video.use_native_backlight=1"
```
```
sudo update-grub
```

If that doesn't work, you may need to add a file
```
sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf
``` And enter this
```
[COLOR=#000000][FONT=Ubuntu Mono]Section "Device"[/FONT][/COLOR]       
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```
and reboot

---

### Post by MrMe01 on 2014-07-15
I updated grub and that worked. The file '20-intel.conf' doesn't exist on my machine. Not in that folder anyway.

Thank you for your help :)

EDIT, I have off as an option! That's awesome!

---

### Post by WinEunuchs2Unix on 2014-07-15
FTR I just tried:

```
[COLOR=#000000][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video.use_native_backlight=1"[/FONT][/COLOR]
```

and I still have 7 brightness levels instead of 10 when rebooting.

Intel Centrino Core 2 Duo T5250 2 Ghz, GME965 Express Chipset w/GPU (like the 3500) running i915 Linux driver.  Toshiba ACPI.  ECHO 4 in startup applications used to have  reasonable brightness on boot up but xrandr for the WVGA  output to external TV kind of ruined that.

---

### Post by jeremy31 on 2014-07-16
You could try adding ```
acpi_osi=linux
``` to the Grub CMDLINE and see if it changes on a reboot.  The number of brightness levels is usually reported to the OS from BIOS during startup after BIOS inquires what OS, Linux ignores the OS request by default

---

### Post by WinEunuchs2Unix on 2014-07-16
> **jeremy31 said:**
> You could try adding ```
acpi_osi=linux
``` to the Grub CMDLINE and see if it changes on a reboot.  The number of brightness levels is usually reported to the OS from BIOS during startup after BIOS inquires what OS, Linux ignores the OS request by default

It does use Linux drivers for some ACPI stuff but it also uses Toshbia ACPI for hot keys that don't work until after a suspend / resume.  I think it uses a generic Linux video driver but it also uses an Intel i915 GPU based graphics driver too.  I did play around with GRUB a couple months ago when first venturing into Ubuntu but I've got higher priority stuff on the go.

I did upgrade GRUB with your recommendation and will post back later if successful.  Thank you.

---

### Post by jeremy31 on 2014-07-17
If it doesn't work, there are plenty of other options that can be tried with acpi_osi=
You might have to use one of the Windows options to get the backlight to give you the 10 steps

---

### Post by WinEunuchs2Unix on 2014-07-17
After reboot it is still at 7 steps of brighness.  I do have a PPA utility called "Brightness Controller" that allows what seems to be 100 levels of brightness control all the way down to blackness.  However a it only turns the brightness down and never back up again.  Brightness control isn't really a burning issue with me...

---

### Post by dave157 on 2014-12-04
moved

---

