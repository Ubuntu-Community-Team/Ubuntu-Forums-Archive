---
title: "Bluetooth on Acer Aspire 5500"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by Sysyphos on 2007-01-16
Hi everyone!
I have installed lots of time ago Ubunto over my Acer Aspire 5500. Now I tried to make the integrate Bluetooth device work. Quite strangely, while pscan works very well (I am able to send everything to my phone and make connections too), i can't make iscan work, so I can't send anything from my phone :(.

I thank everyone who could help me

Some informations:
My hcid.conf file:
#
# HCI daemon configuration file.
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        # none - Security manager disabled
        # auto - Use local PIN for incoming connections
        # user - Always ask user for a PIN
        #
        security auto;

        # Pairing mode
        pairing multi;


        # Default PIN code for incoming connections
        pin_helper /usr/bin/bluez-pin;
}

# Default settings for HCI devices
device {

        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        class 0x3e0100;

        # Inquiry and Page scan
        iscan enable; pscan enable;

        # Default link mode
        lm accept;

        # Default link policy
        lp rswitch,hold,sniff,park;

        iscan enable;

        # Authentication and Encryption (Security Mode 3)
        # auth enable;
        # encrypt enable;
}

hciconfig output:
hci0:   Type: USB
        BD Address: 00:14:A4:FD:06:75 ACL MTU: 1017:8 SCO MTU: 64:8
        UP RUNNING PSCAN 
        RX bytes:1805 acl:0 sco:0 events:40 errors:0
        TX bytes:906 acl:0 sco:0 commands:40 errors:0

---

