---
title: "Bluetooth not recognized"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by ickyfeet on 2007-01-22
I have a kensington USB bluetooth adapter that won't work after a edgy reinstall.  It worked at one point but doesn't any more.   I've tried:

sudo /etc/init.d/bluetooth stop
sudo /etc/init.d/bluetooth start

hcitool dev

and I recieve the following:

Device:

It just doesn't pick it up.  I'm not sure where to go from here.  Any help would be much appreciated.  Oh, I've got all the bluez packages installed.

---

### Post by djf_jeff on 2007-01-22
Can you post the content of the file /etc/defaults/bluetooth please?

I think your problem is in that file but I cannot say where precisely.

---

### Post by ickyfeet on 2007-01-22
Here are the contents of /etc/default/bluetooth as requested:

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
HIDD_ENABLED=0
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
# [http://bluez.sourceforge.net/contrib/HOWTO-PAN](http://bluez.sourceforge.net/contrib/HOWTO-PAN)
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


Thank you for taking the time to try to help . . .

---

### Post by djf_jeff on 2007-01-23
I think the problem is the HIDD server. Change the line :

HIDD_ENABLED=0

for :

HIDD_ENABLED=1

And restart the bluetooth service with :

/etc/init.d/bluetooth restart

---

### Post by ickyfeet on 2007-01-23
I edited the line so that it hidd was enabled and restarted bluetooth using "sudo /etc/init.d/bluetooth restart" and it still did not work.  I also rebooted the computer all together and it still doesn't show my bluetooth adapter.  :(

---

### Post by djf_jeff on 2007-01-23
Can you post the last line from your /var/log/messages with :

tail -n 15 /var/log/messages

Please check to make sure there is no private information before posting this!

---

### Post by ickyfeet on 2007-01-23
Jan 23 18:10:27  -- MARK --
Jan 23 18:30:27  -- MARK --
Jan 23 18:50:27  -- MARK --
Jan 23 19:08:53  kernel: [17185497.968000] cdrom: This disc doesn't have any tracks I recognize!
Jan 23 19:14:58 kernel: [17185863.076000] scsi: unknown opcode 0x01
Jan 23 19:30:27 -- MARK --
Jan 23 19:50:27 -- MARK --
Jan 23 20:10:28 -- MARK --
Jan 23 20:30:28 -- MARK --
Jan 23 20:50:28 -- MARK --
Jan 23 21:10:28 -- MARK --
Jan 23 21:30:28 -- MARK --
Jan 23 21:50:28 -- MARK --

---

### Post by djf_jeff on 2007-01-24
Excuse me to not have been clear enough. Can you redo the same command just after inserting your bluetooth adapter please?

---

### Post by ickyfeet on 2007-01-24
Sorry . . . 


Jan 24 06:40:46 -desktop kernel: [17227010.656000] usb 2-4.3: USB disconnect, address 7
Jan 24 06:40:59 -desktop kernel: [17227022.904000] usb 2-4.3: new full speed USB device using ehci_hcd and address 18
Jan 24 06:40:59 -desktop kernel: [17227023.008000] usb 2-4.3: configuration #1 chosen from 1 choice

---

### Post by djf_jeff on 2007-01-24
Weird, the only difference between your configuration and mine is that your dongle use ehci_hcd and mine une ohci_hcd. I don't know if it's the problem, maybe someone else can help here.

I have check the web and found some things :

- Some ehci_hcd device don't work in USB hub. So be sure to plug the dongle directly in a free port. ([http://bugme.osdl.org/show_bug.cgi?id=4358#c2](http://bugme.osdl.org/show_bug.cgi?id=4358#c2))

---

### Post by ickyfeet on 2007-01-24
I sure as heck don't know what the difference is but I tried to plug the dongle directly into a USB port on the computer and not in the USB hub and SHAZAM! it works . . .  who would have thunk it.  Thanks for the help!

---

### Post by djf_jeff on 2007-01-24
No problem! Personally I don't see the reason either but developer are working on it to fix the problem. For the moment, just use this solution!

---

