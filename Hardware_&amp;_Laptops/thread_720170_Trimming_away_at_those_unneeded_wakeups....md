---
title: "Trimming away at those unneeded wakeups..."
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by Tu13erhead on 2008-03-10
I'm on a Thinkpad x60.  When I run powertop I get

```
<interrupt> : ahci, yenta, i915@pci:0000:00:02.0
```

taking up about 35% of my wakeups.  acpi is next with 25%.

I _think_ the above is due to my CardBus slot.  I don't have anything in the slot and I don't plan to, so if possible I'd like to disable it.

Can anyone provide any advice?  I'd like to get this thing as power friendly as possible.

Also, when running powertop it tells me 4 or so things to do "increase writeback time", something about "noatime", and a couple more.  Is there any way to disable these things automatically upon boot, without having to start up powertop and hit the keys?

Thanks!

---

### Post by Brebs on 2008-03-10
Edit /etc/fstab, e.g.:
```
/dev/sda1  /  ext3  defaults,commit=60,noatime,nodiratime  0  1
```

---

### Post by sdennie on 2008-03-10
You can create a script and toss it into the various /etc/acpi directories (resume.d, start.d, ac.d, battery.d).  Something like this is what I use and it works just fine:

```

$ cat 99-savings.sh 
#!/bin/bash
for x in /tmp/.X11-unix/*; do
        displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
        getXuser;
        if [ x"$XAUTHORITY" != x"" ]; then
            export DISPLAY=":$displaynum"
        if on_ac_power; then
          hdparm -B 255 -S 240 /dev/sda
          echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
          echo 0 > /proc/sys/vm/laptop_mode
          echo 6 > /sys/bus/pci/drivers/iwl3945/0000\:0c\:00.0/power_level
          echo 499 > /proc/sys/vm/dirty_writeback_centisecs
          echo 0 > /sys/module/snd_hda_intel/parameters/power_save
          echo max_performance > /sys/class/scsi_host/host0/link_power_management_policy
           su $user -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 1"
        else
          hdparm -B 128 -S 12 /dev/sda
          echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
          echo 5 > /proc/sys/vm/laptop_mode
          echo 5 > /sys/bus/pci/drivers/iwl3945/0000\:0c\:00.0/power_level
          echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
          echo 10 > /sys/module/snd_hda_intel/parameters/power_save
          echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
           su $user -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 0"
        fi
        fi
done

```

Now, that's a direct copy of what I use and so you would want to edit that I would imagine but, that's the general idea.  One section for when you are on ac power and the other is for battery power.  The big loop around the whole thing is so that I can get the running X users (always just me) and turn on/off compiz sync to vblank.  If you are running an nvidia card and have "OnDemandVBlankInterrupts" set to true in your xorg.conf, turning off sync to vblank in compiz drops the nvidia interrupts in powertop from ~60 to nearly 0.

You can then use a script like this to install your script into the places where it needs to be to handle things like startup/battery/ac/resume:

```

$ cat install_savings.sh 
install 99-savings.sh /etc/acpi/resume.d
install 99-savings.sh /etc/acpi/ac.d
install 99-savings.sh /etc/acpi/battery.d
install 99-savings.sh /etc/acpi/start.d

```

That's what I use.  It's possible that there are cleaner ways but, I've had great luck with this method.  Hope that helps.

---

### Post by Whiffle on 2008-03-10
As for what you're getting from powertop, you could do

modprobe -r yenta_socket 

Also, if you're not using effects on your desktop, you could add the line
        Option          "NoDri"

to the Device section of your /etc/X11/xorg.conf.

---

### Post by Tu13erhead on 2008-03-10
> **Whiffle said:**
> As for what you're getting from powertop, you could do

modprobe -r yenta_socket 

Also, if you're not using effects on your desktop, you could add the line
        Option          "NoDri"

to the Device section of your /etc/X11/xorg.conf.

When using modprobe -r I get "FATAL: Module yenta_socket is in use".  If I recall correctly I can blacklist it and reboot, but I'm wondering why it thinks it's in use...

---

### Post by Tu13erhead on 2008-03-10
I blacklisted uhci_hcd (what should be USB 1), however on reboot it still shows up in powernowd as one of the biggest offenders.  A modprobe -r will get rid of it, but I'm wondering why it starts automatically.

```
  23.5% ( 67.0)       <interrupt> : ahci, i915@pci:0000:00:02.0 
  22.6% ( 64.3)       <interrupt> : ohci1394, HDA Intel, ipw3945 
  15.3% ( 43.7)       <interrupt> : acpi 
```

Those are the biggest offenders now, it seems.  Any suggestions?

---

### Post by ctrlER on 2008-03-14
If you don't use firewire you can rmmod the firewire stuff.

---

