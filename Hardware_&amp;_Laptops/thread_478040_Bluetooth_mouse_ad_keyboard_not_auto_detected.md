---
title: "Bluetooth mouse ad keyboard not auto detected"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by showgun22 on 2007-06-18
I am running the following
XPS M1710 with Ubuntu Feisty 7.04
Int Dell Wireless 350 Bluetooth
Dell Bluetooth Wireless Keyboard & Mouse

rick@rick-laptop:~$ sudo /etc/init.d/bluetooth restart
rick@rick-laptop:~$ sudo hidd --search
Searching ...
        Connecting to device 00:07:61:4E:5B:EF
        Connecting to device 00:07:61:4D:3E:8D

When I try the following I get the connection refused
rick@rick-laptop:~$ sudo hidd --connect 00:07:61:4E:5B:EF
Can't create HID control channel: Connection refused
rick@rick-laptop:~$ sudo hidd --connect 00:07:61:4D:3E:8D
Can't create HID control channel: Connection refused
--connect 00:07:61:4D:3E:8D --connect 00:07:61:4E:5B:EF --server

I have edited the folloing bluetooth file as recommended I amended 
HIDD_ENABLED=1
HIDD_OPTIONS="--connect 00:07:61:4D:3E:8D --connect 00:07:61:4E:5B:EF --server"
I rebooted and same problem nothing is auto detected.
I then found the following link which seems to relate to the problem
[http://blog.heatxsink.com/archives/2006/08/apple_wireless.html]("http://blog.heatxsink.com/archives/2006/08/apple_wireless.html")
I followed their instruction but i am getting into a problem withe the
/etc/bluetooth/hcid.conf
I there is no such line in the Feisty version
can any one guide help me with that one

here is my
rick@rick-laptop:~$ hcitool info 00:07:61:4E:5B:EF
Requesting information ...
        BD Address:  00:07:61:4E:5B:EF
        Device Name: Dell BT Mouse
        LMP Version: 1.2 (0x2) LMP Subversion: 0x545
        Manufacturer: Cambridge Silicon Radio (10)
        Features: 0xfc 0xff 0x0f 0x00 0x08 0x08 0x00 0x00
                <encryption> <slot offset> <timing accuracy> <role switch> 
                <hold mode> <sniff mode> <park state> <RSSI> <channel quality> 
                <SCO link> <HV2 packets> <HV3 packets> <u-law log> <A-law log> 
                <CVSD> <paging scheme> <power control> <transparent SCO> 
                <AFH cap. slave> <AFH cap. master> 
I am incuding the following files bluetooth file and hcid.conf 
Any idea to get this solve?
Thanks

---

### Post by showgun22 on 2007-06-18
I just notice it does auto detect it only has one problem now
If i turn off /shutdown and turn off the mouse than restart the system and turn on the mouse it is being auto detected right away it will also work even if i leave the mouse turned on.
But if I reboot instead of shutting down and do not turn off the mouse it will not auto detect it until I turn off the mouse and turn it back on again.
This is odd and since I am a noob I wonder if I should report that as a bug?

any idea on this one?

---

### Post by kasulstyls on 2007-06-25
showgun22

I was wondering what packages you have installed to get bluetooth to detect your device as, i do the  sudo hidd --search  with no joy at all.


Any help would be greatfull

Thx
kas

---

### Post by danmpem on 2007-07-02
showgun22,
I have been struggling with my bluetooth for a while now, and one of the console commands you posted is part of solving this little mystery.  Could you please post everything you did (that was successful) to get your mouse to work and get on auto-detect?
Thank you

--And even if you don't have "everything", could you post what you have as if you were teaching someone who didn't know anything, because I am somewhat of a newbie.

---

