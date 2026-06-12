---
title: "Hybrid card and enable card on boot"
date: 2013-02-20
forum: Hardware
---

### Post by WiuEmPe on 2013-02-20
Hello, i want to have 2 options in grub: Ubuntu with integrated Intel card, and Ubuntu with Radeon. So i use this initramfs script: ```

#
# Standard initramfs preamble
#
prereqs()
{
:
}

case $1 in
prereqs)
        prereqs
        exit 0
        ;;
esac

# source for log_*_msg() functions, see LP: #272301
. /scripts/functions

#
# Helper functions
#
message()
{
        if [ -x /bin/plymouth ] && plymouth --ping; then
                plymouth message --text="$@"                                                                                                                                
        elif [ -p /dev/.initramfs/usplash_outfifo ] && [ -x /sbin/usplash_write ]; then
                usplash_write "TEXT-URGENT $@"
        else
                echo "$@" >&2
        fi
        return 0
}

run_switcheroo()
{
        local hybridopts
        hybridopts="$1"

        if [ -z "$hybridopts" ]; then
                return 1
        fi

        local IFS=" ,"
        for x in $hybridopts; do
                message "Switching hybrid graphics to $x"
                echo $x > /sys/kernel/debug/vgaswitcheroo/switch
        done
        return 0
}

#
# Begin real processing
#

# Do we have any kernel boot arguments?
for opt in $(cat /proc/cmdline); do
        case $opt in
        hybridopts=*)
                run_switcheroo "${opt#hybridopts=}"
                ;;
        esac
done

exit 0

```

And options in grub:
```

Ubuntu intel - hybridopts=ON,IGD,OFF
Ubuntu radeon - hybridopts=ON,DIS

```

This maybe work, i cant check this becouse after use this script i havent */sys/kernel/debug/vgaswitcheroo/switch* file. 

I want to use close ATI drivers to my Radeon HD 5650, so i install drivers with this method: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installing_via_the_command_line](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Installing_via_the_command_line) and after this i do this: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#WORKAROUND) .

Nextly, i fix problem with difference in xorg.conf: intel hasn't need xord.conf but radeon must have xorg.conf to work. I edit */etc/init/lightdm.conf* and this is content from this file:
```

# LightDM - light Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services
#
# based on gdm upstart script

description     "LightDM Display Manager"
author          "Robert Ancell <robert.ancell@canonical.com>"

start on ((filesystem
           and runlevel [!06]
           and started dbus
           and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
                or stopped udev-fallback-graphics))
          or runlevel PREVLEVEL=S)

stop on runlevel [016]

emits login-session-start
emits desktop-session-start
emits desktop-shutdown

script
    for ARG in $(cat /proc/cmdline); do
        if echo "$ARG" | grep -q "hybridopts"
        then 
          if echo "$ARG" | grep -q "IGD"
          then
            cp /etc/X11/xorg.conf.intel /etc/X11/xorg.conf
          elif echo "$ARG" | grep -q "DIS"
          then
            cp /etc/X11/xorg.conf.radeon /etc/X11/xorg.conf
          fi
        fi
    done
    if [ -n "$UPSTART_EVENTS" ]
    then
        # Check kernel command-line for inhibitors, unless we are being called
        # manually
        for ARG in $(cat /proc/cmdline); do
            if [ "$ARG" = "text" ]; then
                plymouth quit || : 
                stop
                exit 0
            fi
            if echo "$ARG" | grep -q "hybridopts"
            then 
              if echo "$ARG" | grep -q "IGD"
              then
                cp /etc/X11/xorg.conf.intel /etc/X11/xorg.conf
              elif echo "$ARG" | grep -q "DIS"
              then
                cp /etc/X11/xorg.conf.radeon /etc/X11/xorg.conf
              fi
            fi
        done

        [ ! -f /etc/X11/default-display-manager -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/bin/lightdm" -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/sbin/lightdm" ] || { stop; exit 0; }

        if [ "$RUNLEVEL" = S -o "$RUNLEVEL" = 1 ]
        then
            # Single-user mode
            plymouth quit || :
            exit 0
        fi
    fi

    exec lightdm
end script

post-stop script
        if [ "$UPSTART_STOP_EVENTS" = runlevel ]; then
                initctl emit desktop-shutdown
        fi
end script

```

So i add this lines: ```

for ARG in $(cat /proc/cmdline); do
        if echo "$ARG" | grep -q "hybridopts"
        then 
          if echo "$ARG" | grep -q "IGD"
          then
            cp /etc/X11/xorg.conf.intel /etc/X11/xorg.conf
          elif echo "$ARG" | grep -q "DIS"
          then
            cp /etc/X11/xorg.conf.radeon /etc/X11/xorg.conf
          fi
        fi
    done

```

But when i run: Ubuntu Radeon, fglrxinfo return this: 
```
display: :0  screen: 0
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string: 2.1 Mesa 9.0
```

This is my */etc/X11/xorg.conf.radeon*:
```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

What is wrong and how to fix them?

---

