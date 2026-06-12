---
title: "Dual boot bluetooth issues"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by mattskent on 2007-05-24
I'm currently dual booting Vista and Feisty on my Dell Inspiron 6400 laptop (with the built in internal bluetooth card), and I'm having an awful time trying to get my bluetooth mouse working consistently in Ubuntu. Whenever it does work, everything works exactly how it should, and I can get it to connect automatically at start up every time, as long as I don't boot into Vista. The bluetooth card is recognized, and everything works great. When I boot into Vista though and come back to Ubuntu, the card isn't even found. Running "hcitool scan" produces "Device is not available: No such device." Sometimes booting back into Vista, connecting to the mouse, and restarting back into Ubuntu again works to find the card again, and sometimes it doesn't. Any ideas? I copied my /etc/default/bluetooth file below. Let me know if anything else would be relevent.

```

# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.

############ COMPATIBILITY WITH OLD BLUEZ-PAN
# Compatibility: if old PAN config exists, use it
# rather than this file.
if test -f /etc/default/bluez-pan; then
    . /etc/default/bluez-pan
    return
fi
############

############ DUND
#
# Run dund -- this allows ppp logins. 1 for enabled, 0 for disabled.
DUND_ENABLED=0

# Arguments to dund: defaults to acting as a server
DUND_OPTIONS="--listen --persist"

# Run dund --help to see the full array of options.
# Here are some examples:
#
# Connect to any nearby host offering access
# DUND_OPTIONS="--search"
#
# Connect to host 00:11:22:33:44:55
# DUND_OPTIONS="--connect 00:11:22:33:44:55"
#
# Listen on channel 3
# DUND_OPTIONS="--listen --channel 3"

# Special consideration is needed for certain devices. Microsoft
# users see the --msdun option.  Ericsson P800 users will need to
# listen on channel 3 and also run 'sdptool add --channel=3 SP'

############ PAND
#
# Run pand -- ethernet: creates new network interfaces bnep<N>
# that can be configured in /etc/network/interfaces
# set to 1 for enabled, 0 for disabled
PAND_ENABLED=0

# Arguments to pand
# Read the PAN howto for ways to set this up
# http://bluez.sourceforge.net/contrib/HOWTO-PAN
PAND_OPTIONS=""

# example pand lines
#
# Act as the controller of an ad-hoc network
# PAND_OPTIONS="--listen --role GN"
#
# Act as a network access point: routes to other networks
# PAND_OPTIONS="--listen --role NAP"
#
# Act as a client of an ad-hoc controller with number 00:11:22:33:44:55
# PAND_OPTIONS="--role PANU --connect 00:11:22:33:44:55"
#
# Connect to any nearby network controller (access point or ad-hoc)
# PAND_OPTIONS="--role PANU --search"

############ SDPTOOL
# this variable controls the options passed to sdptool on boot, useful if you
# need to setup sdpd on boot.
# options are ;-separated, i.e. for every ; an sdptool instance will be
# launched
#
# examples:
# SDPTOOL_OPTIONS="add --channel=3 SP" # ericsson P800 serial profile
# SDPTOOL_OPTIONS="add --channel=8 OPUSH ; add --channel=9 FTRN" # motorola
#                                             # object push and file transfer
SDPTOOL_OPTIONS=""
```

---

### Post by mattskent on 2007-05-26
Bump

---

### Post by lenticular on 2007-05-27
Not that it helps, but I'm seeing the same behavior on my XP/Feisty dual-boot desktop.  I'm connecting a Logitech dinuvo BT keyboard and mouse.  XP works fine, but I can't make it work in Feisty.  Like you, I find that after I have messed with it it Ubuntu, then XP no longer recognizes my BT keyboard and mouse and I have to add them to the system again.

This is confusing, since I would think that, config-wise, what happens in Feisty stays in Feisty.  

-John

---

### Post by mattskent on 2007-06-14
In case someone stumbles upon this later, I did manage to find a fix for my problem. Apparently the issue was with a firmware upgrade provided by Dell to Windows Vista users, and downgrading the firmware back to the XP version let me use bluetooth as desired in both Vista and Feisty. Here's the thread. The solution I used is in post #7:
[http://ubuntuforums.org/showthread.php?t=378000](http://ubuntuforums.org/showthread.php?t=378000)

---

