---
title: "Problem with accessing cell phone - bluetooth"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by McAviti on 2006-10-20
Hi!

I'd like to synchronize my SE K750 cell phone with kontact. I installed all the required bluetooth package as well as kitchensync and basic communication seems to work. The IrmcSync Connector is finding the K750.
But when starting the sync job i receive the following line in the syslog:
> Oct 21 01:22:42 localhost hcid[7216]: Can't get system message bus name: Connection ":1.11" is not allowed to own the service "org.bluez" due to security policies in the configuration file
My /etc/bluetooth/hcid.conf looks like this:
> 
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
        security auto;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # PIN helper
        pin_helper /usr/bin/pinwrapper;

        # D-Bus PIN helper
        #dbus_pin_helper;
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


Any ideas what i've got to do to some kind of "enable" access to the service?

thanx,
~klemens

---

