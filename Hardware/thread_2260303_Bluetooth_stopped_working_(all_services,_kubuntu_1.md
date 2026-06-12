---
title: "Bluetooth stopped working (all services, kubuntu 14.04)"
date: 2015-01-10
forum: Hardware
---

### Post by 24.cube on 2015-01-10
Hi all,

Sometime in the past couple weeks, my bluetooth stopped working.  It was working fine on my freshly installed kubuntu 14.04 system, I didn't use it at all for the past few weeks, don't recall changing anything (but did install the latest updates as they came in) but when I went to use my external speaker yesterday, nothing.

I have looked through all the forum and bug postings I can find, the most telling thing seems to be:

```
$ sudo pactl load-module module-bluetooth-discover 
Failure: Module initialization failed
```

Dunno why this is the case though, and my searches have not turned up anything useful.  In terms of what's happening, I have now removed / purged / re-installed bluez, bluez-alsa and bluedevil. I can open the 'configure bluetooth' gui via the bluetooth applet, I can find my speaker (or mobile phone or any number of other things), but I cannot connect to anything (the new connection wizard simply hangs forever, and the device disappears from the device list.

I am attaching the output of hcidump -XYt to provide some more enlightening information, hopefully somebody out there can make some sense of things. Below are the logs generated via restarting the bluetooth service, and then attempting to connect my speaker.

```
$udo hcidump -XYtHCI sniffer - Bluetooth packet analyzer ver 2.5
device: hci0 snap_len: 1500 filter: 0xffffffffffffffff
2015-01-11 11:38:58.562897 < HCI Command: Write Extended Inquiry Response (0x03|0x0052) plen 241
    fec 0x00
    Complete local name: 'kubuntu-0'
    TX power level: 0
    Complete service classes: 0x112d 0x1112 0x111f 0x111e 0x110c 0x110e
2015-01-11 11:38:58.565502 > HCI Event: Command Complete (0x0e) plen 4
    Write Extended Inquiry Response (0x03|0x0052) ncmd 1
    status 0x00
2015-01-11 11:38:58.565518 < HCI Command: Write Class of Device (0x03|0x0024) plen 3
    class 0x600100
2015-01-11 11:38:58.566497 > HCI Event: Command Complete (0x0e) plen 4
    Write Class of Device (0x03|0x0024) ncmd 1
    status 0x00
2015-01-11 11:38:58.566527 < HCI Command: Write Class of Device (0x03|0x0024) plen 3
    class 0x640100
2015-01-11 11:38:58.567498 > HCI Event: Command Complete (0x0e) plen 4
    Write Class of Device (0x03|0x0024) ncmd 1
    status 0x00
2015-01-11 11:38:58.567514 < HCI Command: Write Extended Inquiry Response (0x03|0x0052) plen 241
    fec 0x00
    Complete local name: 'kubuntu-0'
    TX power level: 0
    Complete service classes: 0x112d 0x1112 0x111f 0x111e 0x110c 0x110e 0x110b
2015-01-11 11:38:58.569501 > HCI Event: Command Complete (0x0e) plen 4
    Write Extended Inquiry Response (0x03|0x0052) ncmd 1
    status 0x00
2015-01-11 11:38:58.580952 < HCI Command: Write Class of Device (0x03|0x0024) plen 3
    class 0x740100
2015-01-11 11:38:58.582508 > HCI Event: Command Complete (0x0e) plen 4
    Write Class of Device (0x03|0x0024) ncmd 1
    status 0x00
2015-01-11 11:38:58.582537 < HCI Command: Write Extended Inquiry Response (0x03|0x0052) plen 241
    fec 0x00
    Complete local name: 'kubuntu-0'
    TX power level: 0
    Complete service classes: 0x112d 0x1112 0x111f 0x111e 0x110c 0x110e 0x110b 0x1105
2015-01-11 11:38:58.584507 > HCI Event: Command Complete (0x0e) plen 4
    Write Extended Inquiry Response (0x03|0x0052) ncmd 1
    status 0x00
2015-01-11 11:38:58.584626 < HCI Command: Write Extended Inquiry Response (0x03|0x0052) plen 241
    fec 0x00
    Complete local name: 'kubuntu-0'
    TX power level: 0
    Complete service classes: 0x112d 0x1112 0x111f 0x111e 0x110c 0x110e 0x110b 0x1105 0x1106
2015-01-11 11:38:58.587510 > HCI Event: Command Complete (0x0e) plen 4
    Write Extended Inquiry Response (0x03|0x0052) ncmd 1
    status 0x00
2015-01-11 11:39:19.616224 < HCI Command: Inquiry (0x01|0x0001) plen 5
    lap 0x9e8b33 len 8 num 0
2015-01-11 11:39:19.617372 > HCI Event: Command Status (0x0f) plen 4
    Inquiry (0x01|0x0001) status 0x00 ncmd 1
2015-01-11 11:39:19.976428 > HCI Event: Extended Inquiry Result (0x2f) plen 255
    bdaddr 88:C6:26:*:*:* mode 1 clkoffset 0x5d58 class 0x240404 rssi -48
    Unknown type 0x10 with 8 bytes data
    TX power level: 4
    Shortened service classes: 0x110d 0x110b 0x110a 0x110e 0x110f 0x111e
    Complete local name: 'UE BOOM'
2015-01-11 11:39:23.623378 < HCI Command: Inquiry Cancel (0x01|0x0002) plen 0
2015-01-11 11:39:23.625346 > HCI Event: Command Complete (0x0e) plen 4
    Inquiry Cancel (0x01|0x0002) ncmd 1
    status 0x00
2015-01-11 11:39:23.634543 < HCI Command: Create Connection (0x01|0x0005) plen 13
    bdaddr 88:C6:26:*:*:* ptype 0xcc18 rswitch 0x01 clkoffset 0x0000
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 
2015-01-11 11:39:23.636331 > HCI Event: Command Status (0x0f) plen 4
    Create Connection (0x01|0x0005) status 0x00 ncmd 1
2015-01-11 11:39:26.428439 > HCI Event: Connect Complete (0x03) plen 11
    status 0x00 handle 12 bdaddr 88:C6:26:*:*:* type ACL encrypt 0x00
2015-01-11 11:39:26.428663 < HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
    handle 12
2015-01-11 11:39:26.431373 > HCI Event: Page Scan Repetition Mode Change (0x20) plen 7
    bdaddr 88:C6:26:*:*:* mode 1
2015-01-11 11:39:26.432318 > HCI Event: Command Status (0x0f) plen 4
    Read Remote Supported Features (0x01|0x001b) status 0x00 ncmd 1
2015-01-11 11:39:26.433334 > HCI Event: Read Remote Supported Features (0x0b) plen 11
    status 0x00 handle 12
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x59 0x87
2015-01-11 11:39:26.433393 < HCI Command: Read Remote Extended Features (0x01|0x001c) plen 3
    handle 12 page 1
2015-01-11 11:39:26.435325 > HCI Event: Max Slots Change (0x1b) plen 3
    handle 12 slots 5
2015-01-11 11:39:26.437409 > HCI Event: Command Status (0x0f) plen 4
    Read Remote Extended Features (0x01|0x001c) status 0x00 ncmd 1
2015-01-11 11:39:26.444437 > HCI Event: Read Remote Extended Features (0x23) plen 13
    status 0x00 handle 12 page 1 max 1
    Features: 0x01 0x00 0x00 0x00 0x00 0x00 0x00 0x00
2015-01-11 11:39:26.444536 < HCI Command: Remote Name Request (0x01|0x0019) plen 10
    bdaddr 88:C6:26:*:*:* mode 2 clkoffset 0x0000
2015-01-11 11:39:26.444562 < ACL data: handle 12 flags 0x00 dlen 10
    L2CAP(s): Info req: type 2
2015-01-11 11:39:26.446422 > HCI Event: Command Status (0x0f) plen 4
    Remote Name Request (0x01|0x0019) status 0x00 ncmd 1
2015-01-11 11:39:26.448391 > HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 1
2015-01-11 11:39:26.467362 > HCI Event: Remote Name Req Complete (0x07) plen 255
    status 0x00 bdaddr 88:C6:26:*:*:* name 'UE BOOM'
2015-01-11 11:39:30.454874 < ACL data: handle 12 flags 0x00 dlen 12
    L2CAP(s): Connect req: psm 1 scid 0x0040
2015-01-11 11:39:30.459415 > HCI Event: Number of Completed Packets (0x13) plen 5
    handle 12 packets 1
2015-01-11 11:40:00.869138 > HCI Event: Disconn Complete (0x05) plen 4
    status 0x00 handle 12 reason 0x13
    Reason: Remote User Terminated Connection
```

EDIT:

OK, the pactl load-module command failed as the module is already loaded--I was trying that solution as it seemed to be the most popular fix going according to Dr. google...

However, what I have been able to deduce is that I cannot pair with anything--I've tested a macbook, two different android phones, an external speaker, and two headsets (yeah, there's a lot of junk around here...) and the problem is consistent; cannot pair anything.

Any ideas would be greatly appreciated, as this is rather frustrating, especially as the system worked fine only days ago!

---

### Post by 24.cube on 2015-01-15
Solved! With a solution that makes no sense at all...

This machine is triple boot laptop, I booted in to OSX and tried pairing various devices, no problems.  I turned bluetooth off, re-booted into linux, now it works. A truly un-satisfying experience, and I cannot make any sense of it at all.

---

### Post by Sally_Joshua on 2015-01-15
i had the same problem with my wifi drivers not working & i went to windows since i have dual boot and turned wifi on and off, when i went back to ubuntu it was working. & here i thought the systems dont communicate

---

### Post by Re4mRpR on 2015-03-17
i've had similar issues in the last couple years with random wifi routers.  the current one is often after awakening from sleep and then having to restart wireless services, but I had to boot into windows 2 years to get a connection and then reboot back to ubuntu.

---

