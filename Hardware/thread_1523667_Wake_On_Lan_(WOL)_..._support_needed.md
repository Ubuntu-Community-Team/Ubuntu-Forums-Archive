---
title: "Wake On Lan (WOL) ... support needed"
date: 2010-07-04
forum: Hardware
---

### Post by kamelie1706 on 2010-07-04
Hello,

What I want to achieve is simple:
i want my computer to be able to start on demand when I am away. I do not need permanent service on.

What I have done:
- Using Ubuntu 10.04 
- Wake on lan is activated in the motherboard BIOS using the integrated Ethernet connection (ASUS M4A88TD-V)
- Used the script described there
  [http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
- Setup my router to forward the WOL packet to the correct computer (D-LINK DIR-635)
- I use the following service to send the WOL packet
  [http://wakeuponwan.webou.net/](http://wakeuponwan.webou.net/)

What happen:
- I shutdown the computer
- CPU down (no fan anymore)
- graphic card down (no signal to the screen)
- I send the WOL packet immediately 
==> The computer starts :popcorn:

I thought I was done BUT if I wait a bit more after shutdown sending the WOL has no effect :-(

Additional confusion/information
- sudo ifdown eth0 => ifdown: interface eth0 not configured
- sudo ifup eth0 => Ignoring unknown interface eth0=eth0
=> i am sure eth0 is the one used. "ifconfig" returns correct information.
- Bios settings
"Power On from S5 By PME" [enabled]
"Power on From *S5* By *Ring*" [enabled]
"Power on From *S5* By *RTC Alarm*" [disabled]
- Hibernate / Suspend seem not to work (only go to log screen - cpu & graphic card looks to not turn off)

One assumption
- my router assigned the IP dynamically but always the same one to the same computer. Packet forwarding is based on IP and not on MAC address.
- My guess was that when I send the packet short enough after the shutdown of the cpu the network component is still up for a while and the router keep the IP "valid". Then the network card turns off and the router considers the IP invalid and cannot find the computer.

Where should I look for next?
BIOS?
ROUTER?
LINUX?

Thanks

---

### Post by kamelie1706 on 2010-07-04
Here is my /etc/init.d/halt.

WAS
NETDOWN=yes

CHANGED IT TO
NETDOWN=no

TRY
/etc/init.d/halt stop

Same symptoms .... if I send the package within 5 sec after shutdown ok ... more wait no luck!

Am I looking to the right direction?
Should i try to get "power" on by changing "poweroff" option?

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          halt
# Required-Start:
# Required-Stop:
# Default-Start:
# Default-Stop:      0
# Short-Description: Execute the halt command.
# Description:
### END INIT INFO

NETDOWN=no

PATH=/sbin:/usr/sbin:/bin:/usr/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () {
    if [ "$INIT_HALT" = "" ]
    then
        case "$HALT" in
          [Pp]*)
            INIT_HALT=POWEROFF
            ;;
          [Hh]*)
            INIT_HALT=HALT
            ;;
          *)
            INIT_HALT=POWEROFF
            ;;
        esac
    fi

    # See if we need to cut the power.
    if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
    then
        /etc/init.d/ups-monitor poweroff
    fi

    # Don't shut down drives if we're using RAID.
    hddown="-h"
    if grep -qs '^md.*active' /proc/mdstat
    then
        hddown=""
    fi

    # If INIT_HALT=HALT don't poweroff.
    poweroff="-p"
    if [ "$INIT_HALT" = "HALT" ]
    then
        poweroff=""
    fi

    # Make it possible to not shut down network interfaces,
    # needed to use wake-on-lan
    netdown="-i"
    if [ "$NETDOWN" = "no" ]; then
        netdown=""
    fi

    log_action_msg "Will now halt"
    halt -d -f $netdown $poweroff $hddown
}

case "$1" in
  start)
    # No-op
    ;;
  restart|reload|force-reload)
    echo "Error: argument '$1' not supported" >&2
    exit 3
    ;;
  stop)
    do_stop
    ;;
  *)
    echo "Usage: $0 start|stop" >&2
    exit 3
    ;;
esac

:

```

---

### Post by kamelie1706 on 2010-07-04
I guess there is something wrong there

less /proc/acpi/wakeup
```

Device  S-state   Status   Sysfs node
PCE2      S4     disabled  
PCE3      S4     disabled  
PCE4      S4     disabled  
PCE5      S4     disabled  
PCE6      S4     disabled  
PCE7      S4     disabled  
PCE9      S4     disabled  pci:0000:00:09.0
PCEA      S4     disabled  pci:0000:00:0a.0
PCEB      S4     disabled  
PCEC      S4     disabled  
SBAZ      S4     disabled  pci:0000:00:14.2
P0PC      S4     disabled  pci:0000:00:14.4
GEC       S4     disabled  
UHC1      S4     disabled  pci:0000:00:12.0
UHC2      S4     disabled  pci:0000:00:12.2
USB3      S4     disabled  pci:0000:00:13.0
UHC4      S4     disabled  pci:0000:00:13.2
USB5      S4     disabled  pci:0000:00:16.0
UHC6      S4     disabled  pci:0000:00:16.2
UHC7      S4     disabled  pci:0000:00:14.5
PE20      S4     disabled  pci:0000:00:15.0
PE21      S4     disabled  pci:0000:00:15.1
RLAN      S4     disabled  pci:0000:06:00.0
PE22      S4     disabled  
PE23      S4     disabled  
UAR1      S4     disabled  pnp:00:07

```

Which one is my integrated LAN? RLAN?

Found this tutorial
[http://blog.honercek.com/2008/06/wake-up-on-lan-in-linux-system.html](http://blog.honercek.com/2008/06/wake-up-on-lan-in-linux-system.html)

---

### Post by kamelie1706 on 2010-07-04
Now I manage to get
```

Device  S-state   Status   Sysfs node
[B]PCE2      S4     enabled   
PCE3      S4     enabled   
PCE4      S4     enabled   
PCE5      S4     enabled   
PCE6      S4     enabled   
PCE7      S4     enabled   
PCE9      S4     enabled   pci:0000:00:09.0
PCEA      S4     enabled   pci:0000:00:0a.0
PCEB      S4     enabled   
PCEC      S4     enabled   [/B]
SBAZ      S4     disabled  pci:0000:00:14.2
P0PC      S4     disabled  pci:0000:00:14.4
GEC       S4     disabled  
UHC1      S4     disabled  pci:0000:00:12.0
UHC2      S4     disabled  pci:0000:00:12.2
USB3      S4     disabled  pci:0000:00:13.0
UHC4      S4     disabled  pci:0000:00:13.2
USB5      S4     disabled  pci:0000:00:16.0
UHC6      S4     disabled  pci:0000:00:16.2
UHC7      S4     disabled  pci:0000:00:14.5
PE20      S4     disabled  pci:0000:00:15.0
PE21      S4     disabled  pci:0000:00:15.1
**RLAN      S4     enabled   pci:0000:06:00.0**
PE22      S4     disabled  
PE23      S4     disabled  
UAR1      S4     disabled  pnp:00:07

```

Still not working .... ](*,)

---

### Post by kamelie1706 on 2010-07-04
lspci
```

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

Sounds like my hardware is not WOL friendly .....
[http://www.mythtv.org/wiki/Wake-on-LAN](http://www.mythtv.org/wiki/Wake-on-LAN)

---

### Post by kamelie1706 on 2010-07-04
when I try to install the driver from realtek & run autorun I get
```

Check old driver and unload it.
rmmod r8169
Build the module and install
/home/cyril/Downloads/r8168-8.018.00/src/r8168_n.c: In function ‘rtl_get_eeprom’:
/home/cyril/Downloads/r8168-8.018.00/src/r8168_n.c:1794: warning: ‘ret’ may be used uninitialized in this function
[: 48: r8168: unexpected operator
Depending module. Please wait.
load module r8168
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Completed.

```

Not sure if anything really wrong there ...

---

### Post by kamelie1706 on 2010-07-04
Linux version 2.6.32-23-generic
Driver from realtek (latest version) r8168-8.018.00

lspci -v
```

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 83a3
    Flags: bus master, fast devsel, latency 0, IRQ 29
    I/O ports at e800 [size=256]
    Memory at fdfff000 (64-bit, prefetchable) [size=4K]
    Memory at fdff8000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at febf0000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [b0] MSI-X: Enable- Mask- TabSize=4
    Capabilities: [d0] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8168
    Kernel modules: r8168

```latest version of /etc/init.d/halt
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          halt
# Required-Start:
# Required-Stop:
# Default-Start:
# Default-Stop:      0
# Short-Description: Execute the halt command.
# Description:
### END INIT INFO

# CHANGED BY CYRIL 2010-07-04
# NETDOWN=yes
NETDOWN=no

PATH=/sbin:/usr/sbin:/bin:/usr/bin
[ -f /etc/default/halt ] && . /etc/default/halt

. /lib/lsb/init-functions

do_stop () {
    if [ "$INIT_HALT" = "" ]
    then
        case "$HALT" in
          [Pp]*)
            INIT_HALT=POWEROFF
            ;;
          [Hh]*)
            INIT_HALT=HALT
            ;;
          *)
            INIT_HALT=POWEROFF
            ;;
        esac
    fi

    # See if we need to cut the power.
    if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
    then
        /etc/init.d/ups-monitor poweroff
    fi

    # Don't shut down drives if we're using RAID.
    hddown="-h"
    if grep -qs '^md.*active' /proc/mdstat
    then
        hddown=""
    fi

    # If INIT_HALT=HALT don't poweroff.
    poweroff="-p"
    if [ "$INIT_HALT" = "HALT" ]
    then
        poweroff=""
    fi

    # Make it possible to not shut down network interfaces,
    # needed to use wake-on-lan
    netdown="-i"
    if [ "$NETDOWN" = "no" ]; then
        netdown=""
    fi

    log_action_msg "Will now halt"
    
    # ADDED BY CYRIL 2010-07-04
    /usr/sbin/ethtool -s eth0 wol g       # This sets the WOL options on the NIC you may wish to use different ones
    sleep 10                              # Apparently this is necessary
    
    halt -d -f $netdown $poweroff $hddown
}

case "$1" in
  start)
    # No-op
    ;;
  restart|reload|force-reload)
    echo "Error: argument '$1' not supported" >&2
    exit 3
    ;;
  stop)
    do_stop
    ;;
  *)
    echo "Usage: $0 start|stop" >&2
    exit 3
    ;;
esac

:

```

I have also stopped network-manager before shutdown 
service network-manager stop

no progress ... anyone?

PS: should my post better be in network forum?

---

### Post by kamelie1706 on 2010-07-08
Hi,

looks like this is a router limitation. I have managed to wake-up my computer using only the mac adress from the same subnet.

Any idea how to set-up dlink to do the same without IP? Any linux distribution for dlink?

---

