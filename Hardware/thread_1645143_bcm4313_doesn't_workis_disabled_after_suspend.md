---
title: "bcm4313 doesn't work/is disabled after suspend"
date: 2010-12-14
forum: Hardware
---

### Post by dr_oliver on 2010-12-14
Hello Everyone,

I've installed Kubuntu 10.10 on a friends Lenovo B560 notebook and I ran into a Problem I can't solve by myself.

It has a Broadcom bcm4313 wifi chip and it works fine with Ndiswrapper and the restricted STA driver from Broadcom (module 'wl'). So I can connetct to my protected wireless network through NetworkManager or manually by using iwconfig and dhclient.

The Notebook has a LED that indicates if the wifi device is on or off.
Loading/unloading the module turns on/off the device and the LED.

The Problem is that the LED keeps off after resuming from suspend (to disk or ram) and the bcm4313 seems th be 'disabled'. No matter what module I'm using.
Means the interface (eth1 or wlan0 - depending on ndiswrapper or wl) exists after resuming but I can't scan or connect to any network.

I'm using the wl module right now, and this is what dmesg says about the bcm4313 after resuming from suspend to disk (which btw works fine in all other aspects)
```

[  268.179474] eth1: no IPv6 routers present
[  292.422057] wl 0000:04:00.0: PCI INT A disabled
[  296.270871] wl 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  296.270887] wl 0000:04:00.0: setting latency timer to 64
[  296.285833] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36

```

I'm not sure if it could be the PM scripts fault.
because
```

od@minion:~$ dmesg |grep -i 'pm: resume'

```
doesn't mention the wifi:
```

[    1.112810] PM: Resume from disk failed.
[  134.370932] PM: resume of drv:i915 dev:0000:00:02.0 complete after 176.290 msecs
[  134.381669] PM: resume of drv:usb dev:1-1 complete after 179.705 msecs
[  134.381710] PM: resume of drv:hub dev:1-1:1.0 complete after 179.743 msecs
[  134.556490] PM: resume of drv:battery dev:PNP0C0A:00 complete after 354.563 msecs
[  134.557098] PM: resume of drv:usb dev:1-1.6 complete after 355.016 msecs
[  134.557119] PM: resume of drv:uvcvideo dev:1-1.6:1.1 complete after 355.024 msecs
[  134.557129] PM: resume of drv:uvcvideo dev:1-1.6:1.0 complete after 355.036 msecs
[  134.710228] PM: resume of drv:usb dev:1-1.3 complete after 508.228 msecs
[  134.710260] PM: resume of drv:usb dev:1-1.3:1.0 complete after 508.249 msecs
[  137.068209] PM: resume of drv:sd dev:0:0:0:0 complete after 2867.188 msecs
[  137.068229] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 2490.267 msecs
[  137.068257] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2867.203 msecs
[  137.074773] PM: resume of devices complete after 2881.379 msecs
[  137.074882] PM: resume devices took 2.880 seconds

```

So I've treid to unload/load the module manually before/after suspend/resume but with no luck. I've got an interface, but can't use it.

The line
```

[  292.422057] wl 0000:04:00.0: PCI INT A disabled

``` 
**EDIT:** Nothing to worry about. I had the wl module unloaded before.
irritated me, and I tried
```

lshw -C Network

```
it gave me this for my wifi card:
```

  *-network DISABLED
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:dd:24:d5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f2500000-f2503fff

```

I guess the big question is: How do I reenable the bcm4313 after suspend?

I'm using the ubuntu-kernel 2.6.35-23-generic.

Please let me know if you need to know more. I'm stuck.

Thanks and regards
Oliver

---

### Post by dr_oliver on 2010-12-14
UPDATE:

I reenabled the bcm4313 by simply bringing up eth1 with:
```

sudo ifconfig eth1 up

```

now
```
lshw -C Network
```
gives me this:
```

  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:dd:24:d5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f2500000-f2503fff


```

But it still doesn't fix my problem and when I reload the wl module it comes back on DISABLED.

```

od@minion:~$ sudo modprobe -r wl 
od@minion:~$ sudo modprobe wl 
od@minion:~$ sudo lshw -C Network

[SNIP]

  *-network DISABLED
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:dd:24:d5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f2500000-f2503fff

```


UPDATE:

I said eth1 exists after resuming, but theres a difference (besides the not working LED) in
```

ifconfig eth1

```
before the suspend:
```

eth1      IEEE 802.11  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:8 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
and after resume:
```

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

So, here's still something broken


UPDATE:


My card now works with the most recent wl driver I compiled from Broadcoms sourcecode.
```

od@minion:~$ dmesg |grep eth1
[    6.961425] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.246.6 

```

After resuming from suspend I just unload, load the wl driver and bring up eth1.

One Problem remained: wireless connections were always disabled in KNetworkManager after suspend. A Bug report on this issue has already been filed (which I can't find right now) against network-manager so it might be fixed some day.

Until then, this works for me:
- unload wl module
- load wl module
- bring up eth1
- restart networking
- restart network-manager
- wait 1 second
- send dbus command to (re)enable wifi

I wrote (found and modified) a script that takes care of my wifi after suspend.

```

#!/bin/sh
 
. "${PM_FUNCTIONS}"
 
resume_wifi()
{
        # Remove and reload the module for the wifi card
        modprobe -rf wl
        modprobe wl

        # bring up interface
        ifconfig eth1 up
        
        # restart networking and network-manager
        restart networking
        restart network-manager

        # wait a sec
        sleep 1

        # enables wifi in Networkmanager
        dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:true
}
 
case "$1" in
        thaw|resume)
                resume_wifi
                ;;
        *) exit $NA
                ;;
esac

```

Just put it in /etc/pm/sleep.d/90fixwifi.sh, make it executable and go to sleep :)
Now wifi is always on after suspend, even if it was off before. I'll fix that ...

---

### Post by dr_oliver on 2010-12-16
This is the script including a checkup on wifi state before suspend.

comments and improvements on the script are welcome. I don't like the way passing the state from suspend to resume function by using 
/var/log/pm-suspend.log but don't know how to do any better right now.

```

#!/bin/sh
 
. "${PM_FUNCTIONS}"

suspend_wifi()
{
        #check if wifi is up
        wifi_state=`cat /var/lib/NetworkManager/NetworkManager.state |grep WirelessEnabled | sed s/WirelessEnabled\=//`
        echo 'wifi_state='$wifi_state
}
 
resume_wifi()
{
        # Remove and reload the module for the wifi card
        modprobe -rf wl
        modprobe wl

        # restart network-manager
        restart network-manager

        wifi_state=`tac /var/log/pm-suspend.log |grep -m 1 'wifi_state=' |sed s/wifi_state\=//`
        if [ $wifi_state = 'true' ]
        then
                #bring up wifi interface
                ifconfig eth1 up
                # wait a sec
                sleep 1
                # enables wifi in Networkmanager
                dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:true
        else
                # just to be sure ... disables wifi in Networkmanager
                dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false
                # and brings down wifi interface
                ifconfig eth1 down
        fi
}
 
case "$1" in
        hibernate|suspend)
                suspend_wifi
                ;;

        thaw|resume)
                resume_wifi
                ;;
        *) exit $NA
                ;;
esac

```

---

### Post by aiv on 2011-01-13
Hello, I have Lenovo 560B with bcm4727. The same behaviour after sleep. I tried to execute your script manually and got this output:
~$ Desktop/resume_wifi.sh 
.: 3: : not found

---

### Post by dr_oliver on 2011-01-16
hey aiv,

first, the script needs an argument: hibernate, suspend, thaw or resume.
If you put it in /etc/pm/sleep.d/ it'll be executed with the prober argument, depending on the situation (going to sleep/hibernate or wake up).

to dry-run the script, give it the argument suspend or resume.

second, and that's why it doesn't work when you run it manually, is that "${PM_FUNCTIONS}" isn't defined in your terminal (but it will be during suspend/resume).

If you're having problems, put some echo "FOO" lines in the script and check the system log later.

Hope that helps. (I don't have the B560 anymore)

---

