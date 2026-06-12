---
title: "Cannot change backlight brightness Ubuntu 14.04"
date: 2014-06-05
forum: Hardware
---

### Post by cyrus_the_virus on 2014-06-05
This morning I found that I cannot change the brightness of my Dell XPs 13 laptop's display anymore. I tried the following to change the brightness

- Use keyboard brightness keys
- Run the commands shown below
- Boot with kernel option acpi_backlight=vendor. This resulted in a dell_something folder being present in the /sys/class/backlight folder. Changing the brightness file in that folder does not help.
- Add 'intel_backlight' to xorg.conf
- Set "load legacy option ROM" BIOS option to enabled and "secure boot" to disabled
- Boot with kernel option i915.disable-pch_pwm=0
- Boot from a fresh Ubuntu 12.04 USB stick installation. I can still not control the brightness. Maybe this a hardware problem?

Any ideas why this broke suddendly? I've upgraded from 12.04 to 14.04 in April and till yesterday the brightness keys were working fine.

```

echo 100 > /sys/class/backlight/intel_backlight/brightness
echo 100 > /sys/class/backlight/acpi_video0/brightness

```

Thanks!

---

### Post by madvinegar on 2014-06-05
Try getting into BIOS and change the "Load Legacy Option Rom" to "Enabled".

---

### Post by cyrus_the_virus on 2014-06-05
Thanks for your help. I've tried this but unfortunately it does not work for me. I did some more research and found [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1163720") related bug report. It seems that this is a very common problem.

---

### Post by jeremy31 on 2014-06-05
Cyrus, does the osd for brightness appear on your display when you try the brightness hotkeys?  Do you get any resonse from terminal command ```
acpi_listen
```

---

### Post by cyrus_the_virus on 2014-06-06
Hi Jeremy,

Yes, the OSD brightness appears when I use the hotkeys. The acpi_listen command shows the following:
```

$ acpi_listen
video/brightnessup BRTUP 00000086 00000000
 PNP0C14:00 000000d0 00000000
video/brightnessup BRTUP 00000086 00000000
 PNP0C14:00 000000d0 00000000
video/brightnessdown BRTDN 00000087 00000000
 PNP0C14:00 000000d0 00000000
video/brightnessdown BRTDN 00000087 00000000
 PNP0C14:00 000000d0 00000000
video/brightnessdown BRTDN 00000087 00000000
 PNP0C14:00 000000d0 00000000

```

---

### Post by jeremy31 on 2014-06-06
```
video.use_native_backlight=1
``` in grub without anything other than quiet splash

Your line in /etc/default/grub should be ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video.use_native_backlight=1"
```

---

### Post by cyrus_the_virus on 2014-06-06
I have tried to do that (and run update-grub) but unfortunately it does not help :(

---

### Post by jeremy31 on 2014-06-06
> **cyrus_the_virus said:**
> I have tried to do that (and run update-grub) but unfortunately it does not help :(

I am just wondering what is going on 
```
cat /proc/cmdline
``````
ls /sys/class/backlight
``````
cat /var/log/Xorg.0.log | grep backlight
```

And what exactly did you do to add intel_backlight to xorg.conf?  Where is the file at and what is it named and what does it contain?

Have you run Toz's handy script ```
[COLOR=#000000][FONT=verdana]for interface in /sys/class/backlight/*; do echo $interface; cat $interface/actual_brightness; cat $interface/max_brightness; done[/FONT][/COLOR]
```

---

### Post by cyrus_the_virus on 2014-06-07
I used [this/]("http://itsfoss.com/fix-brightness-ubuntu-1310/") article that suggests making a change in xorg.conf. I removed this later because it does solve my problem. I think it just tells to which file the brightness value should be echoed, but since echoing a value manually does not work this solution does not work either.

Here is the output of the commands that you gave me:

```

$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=4e04ddb0-3020-4b02-827f-635306f670db ro quiet splash video.use_native_backlight=1 vt.handoff=7

```

```

$ ls /sys/class/backlight
intel_backlight

```

```

$ cat /var/log/Xorg.0.log | grep backlight
[    11.054] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=4e04ddb0-3020-4b02-827f-635306f670db ro quiet splash video.use_native_backlight=1 vt.handoff=7
[    11.101] (--) intel(0): found backlight control interface intel_backlight (type 'raw')

```

```

$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/intel_backlight
4882
4882

```

Note that this was done with video.use_native_backlight=1

---

### Post by cyrus_the_virus on 2014-06-07
I used [this/]("http://itsfoss.com/fix-brightness-ubuntu-1310/") article that suggests making a change in xorg.conf. I removed this later because it does solve my problem. I think it just tells to which file the brightness value should be echoed, but since echoing a value manually does not work this solution does not work either.

Here is the output of the commands that you gave me:

```

$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=4e04ddb0-3020-4b02-827f-635306f670db ro quiet splash video.use_native_backlight=1 vt.handoff=7

```

```

$ ls /sys/class/backlight
intel_backlight

```

```

$ cat /var/log/Xorg.0.log | grep backlight
[    11.054] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=4e04ddb0-3020-4b02-827f-635306f670db ro quiet splash video.use_native_backlight=1 vt.handoff=7
[    11.101] (--) intel(0): found backlight control interface intel_backlight (type 'raw')

```

```

$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/intel_backlight
4882
4882

```

Note that this was done with video.use_native_backlight=1

---

### Post by jeremy31 on 2014-06-07
> **cyrus_the_virus said:**
> I used [this/]("http://itsfoss.com/fix-brightness-ubuntu-1310/") article that suggests making a change in xorg.conf. I removed this later because it does solve my problem. I think it just tells to which file the brightness value should be echoed, but since echoing a value manually does not work this solution does not work either.

Here is the output of the commands that you gave me:

```

$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=4e04ddb0-3020-4b02-827f-635306f670db ro quiet splash video.use_native_backlight=1 vt.handoff=7

```

```

$ ls /sys/class/backlight
intel_backlight

```

```

$ cat /var/log/Xorg.0.log | grep backlight
[    11.054] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=4e04ddb0-3020-4b02-827f-635306f670db ro quiet splash video.use_native_backlight=1 vt.handoff=7
[    11.101] (--) intel(0): found backlight control interface intel_backlight (type 'raw')

```

```

$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/actual_brightness; cat $interface/max_brightness; done
/sys/class/backlight/intel_backlight
4882
4882

```

Note that this was done with video.use_native_backlight=1


Have you tried to set the brightness using ```
echo 3500 | sudo tee /sys/class/backlight/intel_backlight/brightness
``` with and without video.use_native_backlight?

It sounds like using the 3.14.5 kernel fixes a backlight bug on the XPS13 per a bug report [https://bugs.freedesktop.org/show_bug.cgi?id=76276](https://bugs.freedesktop.org/show_bug.cgi?id=76276)

---

### Post by cyrus_the_virus on 2014-06-10
Hi, sorry for my late reply.

Today I wanted to look into your latest comments and I found out that the display is completely broken now. There is no backlight at all black even during the initial boot up. So, I think it is safe to assume that this is a hardware problem. I will contact Dell support to send it back for repair.

---

### Post by jeremy31 on 2014-06-10
That isn't good, hopefully Dell will have it fixed and back to you soon

---

### Post by cyrus_the_virus on 2014-06-11
I hope so too. Thanks again for your help with troubleshooting the problem :)

---

### Post by firewireo on 2014-09-26
Hi there!

I don't know whether you solved this problem alread or not but I just upgraded from 12.04 to 14.04 on an Asus N56VZ laptop and I'm having the same problem: my Fn+F5 or Fn+F6 keys are not adjusting the brightness, so I googled and googled and found the suggestions of adding /usr/share/X11/xorg.conf.d/20-intel.conf file. and the suggestion to add some lines in your grub after "quiet splash"....
I did all that and non worked!! then I noticed that my graphics isn't showing Inte in "settings>details>graphics" it was showing Gallium!!... anyways... I decided to start over and delete the files that I added in /usr/share/X11/xorg.conf.d/20-intel.conf as well as delete the line after "quiet splash" in grub, and whilst i was at it, I also deleted "nomodeset" line from the grub. I don't even know why it's there to begin with, it shouldn't be there! and by the way I was updating grub and restaring all the time, nothing worked, then I finally started in recovert mode and chose "failsafe graphic" and switched to "...generic..." , restarted one more time and VOILA Function key works!, I went to settings>details and graphics say Intel Ivy bridge!!!
I have no idea what the hell was that all about but it's working now!
One more thing that I noticed before running in recovery mode: everytime I ran "ls /sys/class/backlight" it showed asus-nb-wmi
but after recovery when I booted in normal and ran  "ls /sys/class/backlight" it showed "intel_backlight"

Sorry for rather long reply, I'm hoping my experience can benefit the developer and give them a clue as to what was causing the bug.

Best of luck

---

