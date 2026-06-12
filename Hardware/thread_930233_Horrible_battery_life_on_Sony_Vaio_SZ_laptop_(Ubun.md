---
title: "Horrible battery life on Sony Vaio SZ laptop (Ubuntu 8.04)"
date: 2008-09-25
forum: Hardware
---

### Post by ElectroGrav on 2008-09-25
I'm a long time Windows user who's interested in giving linux a try, so I downloaded Ubuntu 8.04 x86 and ran it in live CD mode on my Sony Vaio SZ750 laptop.

Seemed pretty nice (it detected my wireless, etc.), but there were three serious issues that result in horrible battery life (2-3 hours on a laptop that gets 5-6 hours in Vista), which if not solved, will unfortunately make Ubuntu impossible to use on my laptop:

- There appears to be no way of dimming the screen from it's maximum (which not only drains battery, but hurts my eyes on 100%), not only by the Fn+F5/F6 controls availible under windows, but under any power saving option I could find. Even checking the "reduce screen brightness" option in Ubuntu's power management window has no effect.

- There appears to be no way of downclocking the CPU while on battery like Vista does. I didn't find any power profile or anything like it in the power management window.

- I don't know how to set it up to disable WLAN, WWAN, bluetooth, the optical drive, ethernet port, etc. when not needed also.

As a result of these, Ubuntu draws 20+ watts when idle! Windows Vista usually draws 8 - 12 depending on what I'm doing. Needless to say, this causes a reduction in battery life, more heat production, and overall more stress and wear on my computer. I was hoping Linux would reduce this, not increase it :D

Relevant specs are:
- Intel Core 2 Duo T8100 2.1GHz 3MB L2
- 2 GB RAM (DDR2 667mhz)
- Dual video cards - Intel GMA X3100 / GeForce 8400m gs, one is activated by the BIOS I believe, depending on the setting of the "Stamina / Speed" switch. During my tests I had the Intel GMA X3100 activated.

P.S. I also have an unrelated, noncritical question. It seems in Ubuntu, website text using Sans-serif fonts use some kind of Serif font!?!? I can understand a slight difference in font appearance, but swapping between Serif and Sans-serif? Seems a little unusual.

---

### Post by ElectroGrav on 2008-09-28
No ideas? As a Windows user interested in Linux, I'd really like to get this working, so I hope this works out.

If nobody here knows how to solve these problems, can you refer me to a somewhere/somebody who can?

---

### Post by pihhan on 2008-09-28
Basic problems are that sony does not support Linux or Ubuntu in any way. There are no known ways to power off unneeded devices, because developers of linux kernel or ubuntu does not know ways to turn them off. There is some basic support from sony-laptop module, but does not work for every model. It does not have any graphical gui also. My model (VGN-FZ210) for example does not support any device control under linux.

What i can help you with is dimming your screen. At least with intel graphics card (stamina mode), you have option to use xbacklight utility. You have to install xbacklight package from universe repositories (you have to enable universe package source from package manager), then you can install from terminal using command:

sudo apt-get install xbacklight

You can then control your screen dimming by command from terminal:

xbacklight -set 60 

I understand that it is not best and well prepared, even it is not user-friendly too much, but it is like this. I have [guide to get work also hotkeys](http://www.pihhan.info/sony/) for dimming screen, but i understand for beginner with linux it is too much to do or demand.

You might be subject to [bug in xbacklight initialization](https://bugs.launchpad.net/ubuntu/+source/xbacklight/+bug/176888) also, it might not work right after start.

As for CPU frequency setting, it does work for my configuration pretty well by default. I have only 2 speeds supported by my bios - 1.5 and 1 GHz. Default hardy linux kernel does support cpu scaling when needed, it should be on lower frequency when your CPU is not busy and should raise frequency when CPU is busy to speed things up. It can be changed somehow by choosing different governor in linux kernel or using cpufreq package to tune it up, but i never did that, as default behaviour is good for me. You can add applet to your bar to see current cpu frequency.

---

### Post by ElectroGrav on 2008-09-29
Thanks for the reply. I'll probably try that, but I'm just gonna stick with Vista I think (I like it well enough). I'll just accept that Sony doesn't provide drivers for now.

---

### Post by hermanWaldorf on 2008-10-26
Hi, I have the same problem with a sonyvaio SZ61MN. I thought it was the battery, but now I realize it is Ubuntu. Hope something on this issue appears soon. I contacted sony but they do not provide assistance for systems different from Vista

---

### Post by Nepherte on 2008-10-26
I get 3 hours with 100% brightness and 4 hours with brightness dimmed.

You need to install xbacklight:
```
sudo apt-get install xbacklight
```

Unfortunately it is subjected to a bug. To dim brightness you first have to do this:
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
/etc/init.d/acpid restart
```

Afterwards you can use xbacklight:
```
xbacklight -set percentage
```

For more information: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652)

---

### Post by teaker1s on 2008-10-26
[https://wiki.ubuntu.com/PowerManagement]("https://wiki.ubuntu.com/PowerManagement")

look into power management section also cpu scaling

---

### Post by Nepherte on 2008-10-27
You can squeeze out some extra time of your battery with this: [http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

This is an example script I use for my SZ61:
```
#!/bin/bash
# Reset back to normal settings
if on_ac_power; then

  # Turn off the laptop mode disk optimization
  echo 0 > /proc/sys/vm/laptop_mode

  # Manually set the wifi driver to no power savings.
  echo 6 > /sys/bus/pci/drivers/iwl3945/0000:06:00.0/power_level

  # Set kernel dirty page value back to defaul
  echo 10 > /proc/sys/vm/dirty_ratio
  echo 5 > /proc/sys/vm/dirty_background_ratio

  # Only wakeup every 60 seconds to see if we need to write dirty pages
  # By default this is every 5 seconds but, I prefer 60 to reduce disk
  # activity.
  echo 500 > /proc/sys/vm/dirty_writeback_centisecs

  # Disable power saving settings for the hard disk
  hdparm -B 255 -S 12 /dev/sda

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Enable 'hal' from polling your cdrom
  hal-disable-polling --device /dev/sdc0 --enable-polling
 
  # Enable the unused bluetooth interface
  hciconfig hci0 down ; modprobe hci_usb ; modprobe bluetooth

  # Turn off sound card power savings
  echo 0 > /sys/module/snd_hda_intel/parameters/power_save

  # Set maximum brightness
  xbacklight -set 100


# Turn on aggressive power savings
else

  # Set laptop disk write mode
  echo 5 > /proc/sys/vm/laptop_mode

  # Manually set the iwl3945 driver to power savings.
  echo 5 > /sys/bus/pci/drivers/iwl3945/0000:06:00.0/power_level

  # Reduce disk activity by waiting up to 10 minutes before doing writes
  echo 90 > /proc/sys/vm/dirty_ratio
  echo 1 > /proc/sys/vm/dirty_background_ratio
  echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

  # Enable maximum power saving settings for the hard disk
  hdparm -B 1 -S 12 /dev/sda

  # Make sure ondemand governor is set
  echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 

  # Disable 'hal' from polling your cdrom
  hal-disable-polling --device /dev/sdc0

  # Disable the unused bluetooth interface
  hciconfig hci0 down ; rmmod hci_usb ; modprobe -r bluetooth

  # Set sound card power savings
  echo 10 > /sys/module/snd_hda_intel/parameters/power_save

  # Set lower brightness
  xbacklight -set 50


fi
```

---

