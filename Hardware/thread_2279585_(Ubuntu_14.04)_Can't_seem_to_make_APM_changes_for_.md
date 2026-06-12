---
title: "(Ubuntu 14.04) Can't seem to make APM changes for HDD persistent."
date: 2015-05-24
forum: Hardware
---

### Post by Dropdeadfred on 2015-05-24
Okay, a little background on what i'm doing here. I installed Ubuntu 14.04 and noticed that while plugged into AC my laptop gets uncomfortably warm to the touch, specifically over the area my HDD should be residing (near trackpad, between it and the apu.) So, after digging through countless threads I've discovered Gnome-disks-utility APM and set this to mirror the setting for Battery power. I've set it to 128 which is still disabling spindown, so it shouldn't kill my hdd quicker. However, after every reboot, suspend, or switching power supply the changes are reverted back to 254 for AC which makes my hdd just run rampant and heat up. 

So, does anyone know how I can make this change persistent?

---

### Post by tgalati4 on 2015-05-25
Put the command in /etc/rc.local.  Perhaps update the BIOS of the laptop, since ACPI controls the power handling, there may be a bug that needs fixing.

---

### Post by Dropdeadfred on 2015-05-27
Sorry for the late reply. Thanks though, I hope i don't have to end up doing that, but I might. I kept thinking I saw something about "Thermal" on boot, but it flashed so fast. So I finally remembered I can check dmesg and this is what's going on there. I'm guessing it's related since i'm experiencing a warm running machine. 

$dmesg | grep -i thermal

[   13.389171] [drm] Internal thermal controller without fan control
[   17.271208] [drm] Internal thermal controller without fan control
[14731.082917] CPU0: Unexpected LVT thermal interrupt!

I realize though if this is part of a bug or something, this may need moved to another thread. I just don't want to wreck my laptop, but would like to keep my linux partition (and use it). It's last summer's model. So with fairly new hardware I kind of expected I'd face some issues with Linux. Love linux, but isn't worth it if it will wreck my gear. There are definitely some kinks with this model still. I can't run the proprietary AMD drivers since for what ever reason it makes my touchpad go wonky.
Specs:

Manufacturer: Acer
Model: Aspire E5-551g-t0jn
APU: Amd A10-7300 Kaveri (can't seem to find this particular apu in many devices.)
GPU: Radeon R7 m265 (doesn't seem to be enabled in Ubuntu)

---

### Post by tgalati4 on 2015-05-28
So your laptop is getting warm because the fan isn't working correctly.  I would first look for a BIOS upgrade.  Try flashing the latest firmware and see if that fixes the issue.  You can see the hard disk temps by viewing the SMART parameters of the drive.

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

Although rare, it's possible to degrade your hardware by running without fan control.  You would have to do some more research on that.

Since your hardware is new, try running the latest version of Ubuntu.  Newer kernels will sometimes fix these issues.

---

### Post by Dropdeadfred on 2015-06-07
Thanks for that bit of info and sorry about the late reply here. It seemed to magically work it's self out and run cool, and that interrupt was gone, but like all magical fixes.. it's not really fixed. It's just randomly happening now. I did try the latest ubuntu version via liveusb rather than actually installing and it ran the same issues and had that thermal interrupt happening too. The fan does seem to be running however, as i can feel warm air being pushed out, but it never cycles up at all. So, not sure what exactly I should do if anything can be done. I could upgrade to the nonlts version and then upgrade that if there are kernel updates for it.


edit: I've also updated the bios as well since my original post.

---

### Post by tgalati4 on 2015-06-07
You can install lm-sensors and see if the fan speed is displayed.  

```
sudo apt-get install lm-sensors
sensors
```

See if the fan is visible and if so, put a widget on your panel so you can view the speeds in real time.

Has the laptop been dropped?  Perhaps you have a loose heat sink.  If this is an older machine (5 years or more) then perhaps the heat sink paste needs renewing.

---

### Post by Dropdeadfred on 2015-06-07
The laptop is new as of last year and never been dropped. I do have lm-sensors, and it reads back between 40-59C consistently. I haven't seen it approach any temps that seemed dangerous yet, but when I do sensors detect, it can't find any sensors. So, i'm not exactly sure what it's reading back from if it can't find any. I'm assuming the "sensors detect" command just checks for additional sensors and it's reading the two main ones from my apu and gpu. It seems to be random now, opposed to when I first installed. It's just physically hotter to the touch than my windows partition at times. Perhaps windows is able to leverage the gpu fan to help keep it cool.

---

### Post by tgalati4 on 2015-06-07
Open a terminal and post the output of:

```
sensors
cat /etc/modules
```

Depending on what graphics driver you are using, you can set "dynamic clock" on the GPU so it will throttle up and down depending on load.  Windows does this, but it needs to be enabled in linux.  Typically the GPU and CPU share a heatsink and fan, so you may want to research the motherboard configuration.

Try a LiveUSB of the latest version of Ubuntu and try the proprietary AMD drivers.  You may need a newer kernel to get your hardware to run correctly.

---

### Post by amr-maro on 2015-07-28
I have the same laptop Acer Aspire E5-551G-T0KC. I have Ubuntu 14.04.2 + utopic HWE. It gets warm very quickly, but the fan works properly. I can hear it speeds up when CPU temperature reaches 65 degrees C or higher. Battery life is very bad, 3 hours instead of 7 hours in Windows 8.1.

---

