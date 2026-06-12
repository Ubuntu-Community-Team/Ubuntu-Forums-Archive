---
title: "Wireless Not working"
date: 2010-01-22
forum: Hardware
---

### Post by rithvik on 2010-01-22
I have Dell Latitude D610 laptop. I used to have Win XP and installed Ubuntu 9.10 recently. My wirless stopped working after the install. I looked in forums and found some useful tips but nothing resolved.

I ran couple of commands as suggested and following are the details. My wireless interface comes as disabled. I tried hard key Fn + F2, that also does not work. I checked BIOS and Card is set to ON

rithvik@rithvik-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

rithvik@rithvik-laptop:~$ sudo lshw -C network

*-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:4c:c9:63
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by rithvik on 2010-01-23
There are lot of forum answers but the best answer I found best answer - just get Broadcom Driver by going System>Administration>Hardware and get the driver (you need to be wire connected to get it from Internet)

---

### Post by mikewhatever on 2010-01-23
That's an option for those having a wired connection. The rest can use their installation cds.
[http://ubuntuforums.org/showpost.php?p=8090292&postcount=1](http://ubuntuforums.org/showpost.php?p=8090292&postcount=1)

---

### Post by efflandt on 2010-01-23
If **sudo lspci -v** shows it as BCM4311 or BCM4312 and you have a temporary ethernet connection, the Hardware Driver you need to activate is "Broadcom STA" (not B43 which is for other Broadcom wireless).

If you do not have ethernet access, follow the link mikewhatever posted.

Both methods effectively do the same thing.  Note that your wireless device will appear to be an eth# instead of wlan0, but Network Connections should use the proper device for wireless once you crank in your SSID and security settings.  You may then want to uncheck "Auto eth0" from connecting automatically).

---

