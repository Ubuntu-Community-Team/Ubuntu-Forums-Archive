---
title: "Kernel power fix has increased my power consumption."
date: 2012-04-24
forum: Hardware
---

### Post by roobinatube on 2012-04-24
Hi all, I have an issue with aspm.

Before I installed 12.04 I used the pcie_aspm=force boot option and my laptop used around 12W idling. If I didnt use the boot option, power would be at 16W.

With new kernels, the ones with the famous "power regression fix", I'm back at 16W and the boot option doesn't work anymore.

What can I do to get back to 12W?

Thanks
Andrew


P.S. this is not specific to ubuntu, I tried the opensuse and the fedora kernels... exactly the same pattern.

---

### Post by jeffzzen on 2012-04-30
Hello,

I have exactly the same problem.
I'm running 12.04 on a HP nc6320 laptop (Intel Core Duo T2300, Intel 945GM) and it's consuming a ridiculously high amount (**32 Watts while idle**) of power.

Is there any kind of solution for this? Can I downgrade the kernel only?

Thank you very much in advance,
Jeff

---

### Post by roobinatube on 2012-04-30
I compiled my own 3.0 kernel - works great. I'll keep trying the newer ones as updates come though in the hope of a fix :)

Andrew

---

### Post by jeffzzen on 2012-04-30
> **roobinatube said:**
> I compiled my own 3.0 kernel - works great. I'll keep trying the newer ones as updates come though in the hope of a fix :)

Andrew

So the power consumption is back to normal with kernel 3.0 under 12.04? Did you use any specific parameters? I'll give it a go as well.
I tried all readily available kernels from the repos (3.1.5 through 3.3.3) but none of them helped me to go below 32 Watts of power consumption.

Regarding the fix, I have reported the bug ([https://bugs.launchpad.net/ubuntu/+bug/991694]("https://bugs.launchpad.net/ubuntu/+bug/991694")) and I hope it'll be solved  in the near future, as I need the hardware support of the new 3.2 kernel.

---

### Post by roobinatube on 2012-04-30
I downloaded the kernel-source package from 11.10 and compiled that as standard - no tweaking or extra options, I simply dont have the time nor will (although next time I might compile acpi-cpufreq as a module instead of built in so I can undervolt with phc).

You could probably also add the 11.10 repos and install the kernel-image and kernel-headers without compiling.

With the 3.0 kernel *for my laptop* I use the following parameters: nmi_watchdog=0 pcie_aspm=force acpi=force

I have a lenovo g555.

Andrew

---

### Post by x-shaney-x on 2012-04-30
Can I ask where people get the 12W 16W numbers from?
I am concerned about my battery life on ubuntu and it isn't improving.

---

### Post by roobinatube on 2012-04-30
```
sudo apt-get install powertop
sudo powertop
```

---

### Post by x-shaney-x on 2012-04-30
```
The battery reports a discharge rate of 15.8 W
```
Is that what I'm looking for?

---

### Post by roobinatube on 2012-04-30
Thats the one. Powertop is a good tool, if you go to the tab on the right it gives you suggestions as to what is taking up your power.

---

### Post by x-shaney-x on 2012-04-30
I found a script on crunchbang forums that persistently changes all those suggestions to always good.
Yet my "W" number is higher when using it (18.9 last I looked)

---

### Post by roobinatube on 2012-04-30
Yes, I have come across that script before (but I use laptop-mode-tools instead), but I find the biggest difference is actually screen brightness. If I have my screen on 100% brightness the power usage can be up to 18W, if I take it down to 30% I get down to 11/12W. To change the screen brightness...
```
echo 3 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
for 30% brightness. You can also add this to the script you found to dim and brighten the screen on battery/power.

You could also add to the script to change the CPU scaling govenor on battery/power, I set mine to conservative for battery, and ondemand on power.

Andrew

P.S. (W is Watts, a unit of power)

---

### Post by x-shaney-x on 2012-04-30
Yes which makes me wonder why ubuntu does not change brightness on battery by default, the way KDE does?

In fact, it's a pain that manually changing brightness doesn't stick like volume does.  After a reboot it's back to full brightness and really shouldn't need a script to do it.

---

### Post by roobinatube on 2012-04-30
100% agreed, but this is an upstream bug affecting all gnome shells - which includes unity (that ubuntu uses). In theory there is a setting for dimming display brightness to save power, but for me it makes no difference.

---

### Post by x-shaney-x on 2012-04-30
I believe the setting to dim power is what you see when there is no activity for a few seconds and THEN it autodims.
In my case, if there is any inactivity then the lid is closed :)

Incidentally, I have tried a variation on the script with a couple of extra things in it, including switching to powersave, rather than ondemand on battery and now powertop shows 9.7 W.  A very big improvement.

---

### Post by roobinatube on 2012-04-30
It halved?! What else did you add can I ask?

---

### Post by x-shaney-x on 2012-04-30
Well I changed the brightness to a lower degree (30 instead of 50), added a line to disable NMI watchdog and the switch from ondemand to powersave.

It clearly varies depending on what is happening at the time since it currently says 11.9V but still an improvement.

Just in case it helps anyone, here is the script, though note I have to use a different way of changing brightness, though it doesn't always work properly and I have to manually change it (Acer laptop).

```
#!/bin/sh
# A script to enable laptop power saving features for #! & Debian GNU+linux.
# http://crunchbanglinux.org/forums/topic/11954

# List of modules to unload, space seperated. Edit depending on your hardware and preferences.
modlist="uvcvideo"
# Bus list for runtime pm. Probably shouldn't touch this.
buslist="pci i2c"  #spi

case "$1" in
    true)
    # Enable some power saving settings while on battery
       ## disable the nmi watchdog
        echo 0 > /proc/sys/kernel/nmi_watchdog
       # Enable laptop mode
        echo 5 > /proc/sys/vm/laptop_mode
       # Less VM disk activity. Suggested by powertop
        echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
       # Intel power saving
        echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
        echo 1 > /sys/module/snd_hda_intel/parameters/power_save
       # Set backlight brightness to 50%
       ### echo 5 > /sys/devices/virtual/backlight/acpi_video0/brightness
	/usr/bin/intel_backlight 30 
       # Set powersave CPU governor
        for i in 0 1 2 3; do
        	echo powersave > /sys/devices/system/cpu/cpu${i}/cpufreq/scaling_governor
        done
       # USB powersaving
        for i in /sys/bus/usb/devices/*/power/autosuspend; do
            echo 1 > $i
        done
       # SATA power saving
        for i in /sys/class/scsi_host/host*/link_power_management_policy; do
            echo min_power > $i
        done
       # Disable hardware modules to save power
        for mod in $modlist; do
            grep $mod /proc/modules >/dev/null || continue
            modprobe -r $mod 2>/dev/null
        done
        Enable runtime power management. Suggested by powertop.
        for bus in $buslist; do
            for i in /sys/bus/$bus/devices/*/power/control; do
                echo auto > $i
            done
        done
    ;;
    false)
       #Return settings to default on AC power
        echo 0 > /proc/sys/vm/laptop_mode
        echo 500 > /proc/sys/vm/dirty_writeback_centisecs
        echo N > /sys/module/snd_hda_intel/parameters/power_save_controller
        echo 0 > /sys/module/snd_hda_intel/parameters/power_save
        ### echo 10 > /sys/devices/virtual/backlight/acpi_video0/brightness
	/usr/bin/intel_backlight 100
       # Set powersave CPU governor
        for i in 0 1 2 3; do
        	echo ondemand > /sys/devices/system/cpu/cpu${i}/cpufreq/scaling_governor
                done
        for i in /sys/bus/usb/devices/*/power/autosuspend; do
            echo 2 > $i
        done
        for i in /sys/class/scsi_host/host*/link_power_management_policy
            do echo max_performance > $i
        done
        for mod in $modlist; do
            if ! lsmod | grep $mod; then
                modprobe $mod 2>/dev/null
            fi
        done
        for bus in $buslist; do
            for i in /sys/bus/$bus/devices/*/power/control; do
                echo on > $i
            done
        done
    ;;
esac

exit 0
```

Only "bad" thing showing in powertop is my USB mouse.  I can do autosuspend on that but I don't like the lag.

---

### Post by jeffzzen on 2012-05-01
> **roobinatube said:**
> I downloaded the kernel-source package from 11.10 and compiled that as standard - no tweaking or extra options, I simply dont have the time nor will (although next time I might compile acpi-cpufreq as a module instead of built in so I can undervolt with phc).

You could probably also add the 11.10 repos and install the kernel-image and kernel-headers without compiling.

With the 3.0 kernel *for my laptop* I use the following parameters: nmi_watchdog=0 pcie_aspm=force acpi=force

I have a lenovo g555.

Andrew

Now I'm using the 3.0 kernel with the parameters you mentioned and the power consumption dropped a bit, however, it's still pretty high, around 26 Watts. I hope the problem will fixed soon.

I should probably try Shaney's script.

---

### Post by roobinatube on 2012-05-01
Do you have a lenovo G555? Your laptop might be different to mine. In my experience proprietary graphics drivers (especially ATI, not as much nvidia) make a HUGE difference to power consumption. On my laptop with the opensource radeon module my laptop never takes below 20W. Installing the ATI driver (fglrx) almost halves this.

Try finding out what hardware you have and what modules are loaded to run it. Then look those modules up and see if there are any powersaving parameters you can use. Example: the radeon module can run with dynamic clock speed, and to enable that the boot option radeon.dynclks=1 should be added.

Alternatively on ubuntu it suggests the proprietary drivers and installs them for you, which should set everything up all the boot options for you. Just open the application "Additional Drivers".

Andrew

---

### Post by x-shaney-x on 2012-05-01
Hmm, been monitoring things and have found that using the script I posted up, wattage does go lower than it ever does without BUT the wattage also varies wildly with it.

With the script it can be anything from 9.3 to 18.9 (so far).
Without the script it tends to stay between 15 and 18 most of the time.

---

### Post by roobinatube on 2012-05-01
I would say that means aspm is working then, it's dropping the power to your hardware when it doesn't need it, and giving it more when it requires.

if you want to lower the requirements I think your best bet would be to log into Ubuntu 2D or change window manager. other things you can try are increasing readahead to stop your disk spinning up as much, and are you using btrfs? if you use compression you can reduce the amount of disk I/Os. 

Andrew

---

