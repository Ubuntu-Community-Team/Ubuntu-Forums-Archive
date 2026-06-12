---
title: "tx1000 - The final guide."
date: 2011-02-07
forum: Hardware
---

### Post by Alejandro Nova on 2011-02-07
***DISCLAIMER: Thanks to synplague for some Ubuntu-specific bits and general updating of this guide.***

Dear guys at Ubuntu Forums.

The rate of mortality of this laptop is high. For all those surviving tx1000s, and for all those owners who like them and want to stuff them with Ubuntu Maverick Meerkat, here's the final guide I compiled after years of using Linux with this computer.

**Things to install**

With a normal Ubuntu install, there are some choices that you need to make. With the Pavilion tx1000, by far, **the most important one is your video driver**. With a normal laptop, you can, and I'd recommend, install Nouveau. But with the Pavilion tx1000 you **simply can't**. Nouveau doesn't have any form of power management, and this fact combined with severe design flaws in the tx1000 will **burn your NVIDIA southbridge if you use Nouveau**. Install the blob as soon as you can, and do it the Ubuntu way... with the Restricted Drivers manager. Also, you'll enable there the Broadcom wl driver.

Once you have that, let's start tweaking.

**Touchscreen**

Forget about EETI, egalax, touchkit, and the like; we have free drivers and we are going to use them. They work in 32 and 64 bits, and they work well... after some tweaking.

Your /etc/default/grub will contain these lines.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Change them to this.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="usbhid.quirks=0xeef:0x1:0x40"
```

This sequence will enable your kernel to directly see your touchscreen. Confirm it running:

```
sudo update-grub
```

After that, reboot. You'll have a poorly calibrated, but working, touchscreen. Install this PPA, and this package.

```
sudo add-apt-repository ppa:tias/xinput-calibrator-ppa
sudo apt-get update
sudo apt-get install xinput-calibrator
```

After that, let's take the Ubuntu way. Navigate in your Menu, and you'll find an item called "Calibrate Touchscreen". Click on it. You'll see a terminal window and after that, four dots. Press them with your working pen. When calibration is over, pay attention to the final sequence.

```
--> Making the calibration permanent <--
  copy the snippet below into '/etc/X11/xorg.conf.d/99-calibration.conf'
Section "InputClass"
        Identifier      "calibration"
        MatchProduct    "eGalax INC. USB TouchController"
        Option  "Calibration"   "39 4003 124 3974"
EndSection

```

What are we going to do? Paste the snippet indicated by that program (the section beginning with Section "InputClass")... right into your /etc/X11/xorg.conf. You'll get an amazing calibration.

To finish your setup, create an autorotate.sh script and run it at the beginning of your session. This is the script.

```
#!/bin/sh
OLDMODE=$(cat /sys/devices/platform/hp-wmi/tablet)
while true; do
    MODE=$(cat /sys/devices/platform/hp-wmi/tablet)
    if [ "$MODE" != "$OLDMODE" ]
    then
        #echo "$MODE - $OLDMODE"
        case "$MODE" in
            "0")
                # Do something
                echo "Normal mode"
                xrandr -o normal
                xinput set-prop 12 "Evdev Axis Inversion" 0 0
                xinput set-prop 12 "Evdev Axes Swap" 0
                xinput set-prop 13 "Evdev Axis Inversion" 0 0
                xinput set-prop 13 "Evdev Axes Swap" 0
                ;;
            "1")
                # Do something else
                echo "Tablet mode"
                xrandr -o left
                xinput set-prop 12 "Evdev Axis Inversion" 1 0
                xinput set-prop 12 "Evdev Axes Swap" 1
                xinput set-prop 13 "Evdev Axis Inversion" 1 0
                xinput set-prop 13 "Evdev Axes Swap" 1
                ;;
        esac
        OLDMODE=$MODE
    fi
    sleep 3s
done
```

Now, when you flip your screen, your touchscreen will rotate... but you'll get an error, because you still can't rotate your screen. Well... let's take care of that.

**Video**

These lines in your /etc/X11/xorg.conf file will fix the screen rotation, and make some awesome things.

```
Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option  "OnDemandVBlankInterrupts"      "True"
        Option  "RandRRotation" "True"
        Option  "TripleBuffer"  "True"
        Option  "RegistryDwords" "PowerMizerEnable=0x1;PerfLevelSrc=0x3333;PowerMizerLevel=0x3;PowerMizerDefault=0x1;PowerMizerDefaultAC=0x1"
EndSection
```

The RandRRotation line takes care about the screen rotation. But pay attention to another line: RegistryDwords. These are Registry keys fed directly to the NVIDIA driver. We are configuring our GeForce 6150 to work at full speed when on AC, and at 100 MHz when on batteries. This is going to save you a lot of power. Also, the OnDemandVBlankInterrupts line also saves power.

Run this also on start.

```
nvidia-settings -a InitialPixmapPlacement=2
```

This will give you additional speed, and it's needed with the 6150.

**Side keys and power savings**

By default, you have 4 keys in your screen (DVD, QuickPlay, Rotate and Gear) and only one works. This is my /etc/rc.local specially tailored for my tx1000, and this takes care of the DVD key.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Enable some offloading for your network interfaces, saves power!
ethtool -K eth0 gso on
ethtool -K eth1 gso on
ethtool -s eth0 wol d

# This requires the Broadcom WL driver. Saves power!
iwconfig eth1 txpower 20

# This enables the DVD key under X. You can use it now!
setkeycodes e00e 228

# Cheap copy of the WonderPatch
mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent

exit 0
```

Do not forget to follow power saving howtos to get additional power savings.

**The rest?**

Well, works OUT OF THE BOX! That includes the remote, the docking station (if you have one), the function keys, the TV-out, and EVEN THE FINGERPRINT SCANNER. Test and enjoy!

BTW, if you want your fingerprint scanner, don't forget to install (these programs are not needed for it to work, but they make it work as an authentication method):

```
sudo apt-get install fprint-demo libpam-fprint
```

On my Kubuntu install, hibernation didn't work out of the box. Fixing that was easy.

```
sudo apt-get install hibernation uswsusp
```

---

