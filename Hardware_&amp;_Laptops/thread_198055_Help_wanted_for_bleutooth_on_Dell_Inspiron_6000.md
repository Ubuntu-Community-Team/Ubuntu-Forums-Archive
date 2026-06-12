---
title: "Help wanted for bleutooth on Dell Inspiron 6000"
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by justfred on 2006-06-16
Hi,

I'm not able to make the bluetooth work between my Dell Inspiron 6000 and my Sony-Ericsson K750i. 

After searching these and other forums as well as google, I've come to change /etc/dbus-1/system.d/bluez.conf to solve a security policy issue :

[CODE]
~$ ls /etc/dbus-1/system.d/bluez.conf
/etc/dbus-1/system.d/bluez.conf
frederic@insp6000:~$ cat /etc/dbus-1/system.d/bluez.conf
<!-- This configuration file specifies the required security policies
     for bluez-pin to work. -->

<!DOCTYPE busconfig PUBLIC "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>

  <!-- ../system.conf have denied everything, so we just punch some holes -->

  <policy context="default">
    <allow own="org.handhelds.gpe.bluez"/>

    <allow send_destination="org.handhelds.gpe.bluez"/>
    <allow receive_sender="org.handhelds.gpe.bluez"/>

    <allow send_path="/org/handhelds/gpe/bluez/PinAgent"/>
  </policy>

  <policy context="default">
    <allow own="org.bluez.PinAgent"/>

    <allow send_destination="org.bluez.PinAgent"/>
    <allow receive_sender="org.bluez.PinAgent"/>

    <allow send_path="/org/bluez/PinAgent"/>
  </policy>

  <policy user="root">
    <allow own="org.bluez"/>
  </policy>

  <policy at_console="true">
    <allow send_destination="org.bluez.Device"/>
    <allow receive_sender="org.bluez.Device"/>

    <allow send_path="/org/bluez/Device"/>

    <allow send_destination="org.bluez.Manager"/>
    <allow receive_sender="org.bluez.Manager"/>

    <allow send_path="/org/bluez/Manager"/>
  </policy>

</busconfig>
[CODE]

my /etc/bluetooth/hcid.conf now looks like :

[CODE]
$ cat /etc/bluetooth/hcid.conf
#
# HCI daemon configuration file.
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security none;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # PIN helper
        #pin_helper /usr/bin/pinwrapper;
        #pin_helper /usr/bin/bluez-pin;
        #pin_helper /usr/bin/bluepin

        # D-Bus PIN helper
        dbus_pin_helper;
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        class 0x3e0100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;

        # Default link mode
        #   none   - no specific policy
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;

        # Authentication and Encryption (Security Mode 3)
        #auth enable;
        #encrypt enable;
}
[CODE]

and the relevant output in the log is :
[CODE]
Jun 16 21:13:23 localhost hcid[4511]: Bluetooth HCI daemon
Jun 16 21:13:23 localhost hcid[4511]: HCI dev 0 up
Jun 16 21:13:23 localhost sdpd[4516]: Bluetooth SDP daemon
[CODE]

however I cannot detect any bluetooth devices with hcitool :
[CODE]
$ hcitool dev
Devices:
        hci0    00:10:C6:EB:EB:85
$ hcitool scan
Scanning ...
$
[CODE]

and scanning from my K750i also reveals no devices found.

However when scanning using either hcitool or via gnome's Bleutooth manager the small (blue) bluetooth light stays on for a while instead of flashing briefly about every second.

I know my phone can be discovered as this works well within windows XP.

Help appreciated.

---

### Post by sleytr on 2006-09-02
Hi, 

Bluetooth was working last year when I install breezy and play with bluez config files. Than it broken after some apt-get upgrade. Now I have finally upgraded to Dapper and still stucked with  exactly same symptoms with above post. (2.6.15-26-686)

I purged and reinstalled dbus,bluez-utils,hal, blue-pin etc. Nothing worked.

Any help is so appreciated.

---

