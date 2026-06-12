---
title: "Yamaha MD-BT01 bluetooth midi adaptor not sending midi to Ubuntu Studio 18.04"
date: 2019-01-21
forum: Hardware
---

### Post by alangh on 2019-01-21
I have a Kawai K1 synthesizer keyboard with a Yamaha MD-BT01 bluetooth midi adaptor plugged in. A nearby computer running Ubuntu Studio 18.04 has a USB bluetooth dongle (Laird BT851). The problem is no midi ports are visible under ubuntu.

In the GUI for Ubuntu Studio (Settings -> Bluetooth Manager), the Yamaha device is visible, and it has been paired and trusted. 

In my web searches I have noticed someone successfully using a Kawai K1 with a MD-BT01. I have also noticed someone using an MD-BT01 with linux. So it "should" work. What I want to do is transfer sysex sound patches to the Kawai. There are 3 settings on the Kawai K1 that are properly set to receive sysex midi.

For ubuntu apparently 18.04 is the first edition with the bluetooth midi built in by default. See "Ted's Linux MIDI Guide" [http://tedfelix.com/linux/linux-midi.html](http://tedfelix.com/linux/linux-midi.html)

Attempts to investigate by the command line:

```
user1@linuxbox:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 005: ID 05ac:0204 Apple, Inc. 
Bus 005 Device 004: ID 05ac:1002 Apple, Inc. Extended Keyboard Hub [Mitsumi]
Bus 005 Device 003: ID 046d:c001 Logitech, Inc. N48/M-BB48/M-UK96A [FirstMouse Plus]
Bus 005 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 04b4:f901 Cypress Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

user1@linuxbox:~$ lsmod | grep usb
btusb                  45056  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
btintel                16384  1 btusb
bluetooth             548864  51 btrtl,btintel,btbcm,bnep,btusb,rfcomm
usbhid                 49152  0
hid                   118784  2 usbhid,hid_generic

user1@linuxbox:~$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'

user1@linuxbox:~$ aconnect -o
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'

user1@linuxbox:~$ amidi -l
Dir Device    Name

user1@linuxbox:~$ bluetoothctl
[bluetooth]# devices
Device DC:EA:50:2A:52:E7 MD-BT01
[bluetooth]# info  DC:EA:50:2A:52:E7
Device DC:EA:50:2A:52:E7 (random)
    Name: MD-BT01
    Alias: MD-BT01
    Paired: yes
    Trusted: yes
    Blocked: no
    Connected: no
    LegacyPairing: no
    UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
    UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
    UUID: Device Information        (0000180a-0000-1000-8000-00805f9b34fb)
    UUID: Vendor specific           (03b80e5a-ede8-4b33-a751-6ce34ec4c700)


```

---

### Post by alangh on 2019-02-27
This turned out to be a software issue, not hardware. There is a solution posted in the networking & wireless forum: [https://ubuntuforums.org/showthread.php?t=2411315&p=13841006#post13841006](https://ubuntuforums.org/showthread.php?t=2411315&p=13841006#post13841006)

---

