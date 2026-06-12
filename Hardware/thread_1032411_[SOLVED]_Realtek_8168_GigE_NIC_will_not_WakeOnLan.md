---
title: "[SOLVED] Realtek 8168 GigE NIC will not WakeOnLan"
date: 2009-01-06
forum: Hardware
---

### Post by zanophol on 2009-01-06
I have an MSI K9A2-NeoF Motherboard, which has an onboard Realtek 8168 Gigabit Ethernet controller. I have installed Kubuntu 8.10 x64 version. I am attempting to implement WakeOnLan for the ethernet controller. This is a new build, so I don't know if it would have worked on 8.04, as I upgraded the mobo when I installed 8.10.

I have been all over these forums trying different things for this problem, but NOTHING works. I have replaced the default kernel module with the Realtek driver r8168-8.010.00 (downloaded yesterday). The network works, but I cannot WOL. If I simply power off the machine in Kubuntu, WOL works. I have a dual boot with Vista (for games), and WOL works from a Windows shutdown. This tells me Kubuntu is doing something that kills the WOL functionality.

Can anyone help?

Here is where I am at:

1) lspci output: 
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

2) lsmod | grep r8
r8168                  49168  0

3) dmesg | grep eth
[   19.186325] eth0: Identified chip type is 'RTL8168B/8111B'.
[   19.186328] eth0: RTL8168B/8111B at 0xffffc20000c60000, 00:21:85:0a:af:7e, IRQ 2300

4) cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

5) cat /etc/init.d/wakeonlanconfig
#!/bin/bash
ethtool -s eth0 wol g
exit

6) sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes


7) cat /etc/init.d/halt
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
        ifdown --force -a
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

EDIT: I should also note that if I issue the "poweroff -f" command, WOL will work after shutdown.

---

### Post by zanophol on 2009-01-09
bump...I know someone has hit this...

---

### Post by zanophol on 2009-01-12
I kept at it and found this [URL="http://ubuntuforums.org/showthread.php?t=1036399&highlight=intrepid+wol"]link
[/URL] , which led me to try one other thing in addition to what I have tried already.

Essentially, having "NETDOWN=no" in /etc/init.d/halt and "pre-down false" as the last line for eth0 in the /etc/network/interfaces file is what fixed it for me.

---

### Post by sohelmk on 2011-06-20
Hi Zanaphol,
I assume Realtek 8168 is a wireless network card. But I found that it does not support WoWLAN that is essential to wake on lan on wireless card. 

So I wonder how did you get it working, or am I missed something.

Please let me know as I have same card and checking if it can be waked on wireless?

Thank you and Regards,
Sohel
__

---

