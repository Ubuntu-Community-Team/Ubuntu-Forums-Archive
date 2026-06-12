---
title: "IBM X40 Ubuntu or Xubuntu"
date: 2008-10-18
forum: Hardware
---

### Post by Maccer101 on 2008-10-18
Hi,

thinking about buying a second hand X40 thinkpad for around £100, it would have a Centrino 1.2ghz, 512mb RAM & a 40gb HDD, would I be better off installing Xubuntu instead of Ubuntu to get a more responsive system.  Its primary use would be browsing the internet and playing media off my Ubuntu home network.

thanks

---

### Post by fajardo on 2009-03-16
I know it has been almost one year ago but I guess I could have an answer for you.

I'm running ubuntu on my desktop. I have a X40 and I decided to try debian 5 on it. It runs faster, gnome is sluggy but kde3.5 is running quite fine, so I recommend using kde cd installation. 

It installed well. I used the full cd installation.

Issues:
-firmware for ipw2200 (wifi): [http://wiki.debian.org/ipw2200](http://wiki.debian.org/ipw2200)
-opengl isn't installed out of the box: apt-get install libgl1-mesa-dri
-cpu throttling not out of the box:
    -edit /etc/modules
        add the lines: 
           acpi_cpufreq
           cpufreq_ondemand
           cpufreq_userspace
           cpufreq_conservative
           cpufreq_powersave
        after the "loop" entry
    -edit /etc/rc.local
        add after the comments and before exit 0:
           echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
-for the trackpoint: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)
resumed:
    -edit /etc/rc.local
        add after "echo ondemand":
           echo -n 200 > /sys/devices/platform/i8042/serio1/speed
           echo -n 250 > /sys/devices/platform/i8042/serio1/sensitivity
    -edit /etc/X11/xorg.conf
        inside of Section "InputDevice"
                  Identifier "Configured Mouse"
        add the lines:
            Option "EmulateWheel" "on"
            Option "EmulateWheelButton" "2"
        before EndSection

That's all.

---

