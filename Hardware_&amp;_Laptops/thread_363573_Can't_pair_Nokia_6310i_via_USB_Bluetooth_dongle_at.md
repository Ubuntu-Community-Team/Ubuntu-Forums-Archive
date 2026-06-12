---
title: "Can't pair Nokia 6310i via USB Bluetooth dongle at 6.10"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by saepia on 2007-02-17
Hi. I try to use my Nokia 6310i as modem. I can't connect to it because when my phone asks about a PIN number it always fails.

[LIST=1]
[*]My phone is found well by bluetooth dongle
[*]My HCId conf:
```
marcin@saepia:~$ cat /etc/bluetooth/hcid.conf 
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

        # Default PIN code for incoming connections
        passkey "7812";
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
        discovto 0;

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


}

```
[*]Using pin_helper doesn't work - my hcid says that this option is unrecognized.
[*]I don't know why bt-applet is not started with bluetooth services?
[*]What I do (I do those things manually because I am seeking what's wrong):
[LIST=1]
[*]```
marcin@saepia:~$ sudo hcid -n
hcid[7444]: Bluetooth HCI daemon
hcid[7444]: Register path:/org/bluez fallback:1

```
[*]After putting the dongle hcid says:
```

hcid[7444]: HCI dev 0 registered
hcid[7444]: Register path:/org/bluez/hci0 fallback:0
hcid[7444]: HCI dev 0 up
hcid[7444]: Device hci0 has been added
hcid[7444]: Device hci0 has been activated

```
[*]After I run bt-applet hcid says:
```

hcid[7444]: name_listener_add(:1.37)
hcid[7444]: Default passkey agent (:1.37, /org/bluez/applet) registered

```
[*]After I try to do any operation (e.g. pppd call, rfcomm is configured properly) I'm asked on my phone for PIN and it always fails. hcid says something like that (the process have other PID because i closed terminal with old one by my mistake but it always looks like that):
```

hcid[6942]: pin_code_request (sba=11:11:11:11:11:11, dba=00:60:57:33:8B:99)
hcid[6942]: Calling PasskeyAgent.Request: name=:1.28, path=/org/bluez/applet
hcid[6942]: PasskeyAgent.Request(/org/bluez/hci0, 00:60:57:33:8B:99) was canceled
hcid[6942]: Releasing agent :1.28, /org/bluez/applet
hcid[6942]: name_listener_remove(:1.28)
hcid[6942]: Unregister path:/org/bluez/hci0
hcid[6942]: Unregister path:/org/bluez
hcid[6942]: Exit

```
[/LIST]
[*]I found this bugs: [https://launchpad.net/ubuntu/+source/bluez-utils/+bug/56651](https://launchpad.net/ubuntu/+source/bluez-utils/+bug/56651) I think it's related but I can't see any solution for me in it.
[/LIST]

What am I doing wrong?

---

### Post by saepia on 2007-02-17
Sorry, it works, my typo in 1 place caused it to fail :(

---

### Post by pieroxy on 2007-03-16
Would you care to elaborate how you fixed your problem? I have a very similar one and am interested in anything that could help me.

Thanks

---

