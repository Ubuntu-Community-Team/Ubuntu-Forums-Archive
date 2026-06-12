---
title: "Logitech Bluetooth Mouse Not Detected"
date: 2019-07-01
forum: Hardware
---

### Post by mydroog on 2019-07-01
Hey guys!


  My laptop is running Xubuntu 16.04 and I've been having this issue.


  I bought a (pricey) Logitech MX Anywhere 2S wireless mouse, partially  because of the bluetooth capability as USB ports on my laptop are  limited. For some reasons, my laptop can't detect the mouse at all. The  Bluetooth on my laptop is functioning, as it can detect and pair to my  phone. My phone can detect and pair to the mouse. But the Laptop simply  cannot even detect the mouse.

 
I've heard this maybe be related to Bluetooth Low Energy or  something. I've seen tried to load up Xubuntu 18.04.1 on a USB (live  session) but had the same problem - mouse is not detected.

  Any suggestions? Thanks in advance!

PS: "hciconfig -a" brings up the following:


```
Type: BR/EDR  Bus: USB
BD Address: 40:9F:38:C5:A8:48  ACL MTU: 1024:8  SCO MTU: 50:8
UP RUNNING 
RX bytes:729 acl:0 sco:0 events:53 errors:0
TX bytes:4109 acl:0 sco:0 commands:53 errors:0
Features: 0xff 0xfe 0x8f 0xfe 0xd8 0x3f 0x5b 0x87
Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
Link policy: RSWITCH HOLD SNIFF 
Link mode: SLAVE ACCEPT 
Name: 'E203NA'
Class: 0x10010c
Service Classes: Object Transfer
Device Class: Computer, Laptop
HCI Version: 4.1 (0x7)  Revision: 0x0
LMP Version: 4.1 (0x7)  Subversion: 0x25a
Manufacturer: Qualcomm (29)
```

---

### Post by CatKiller on 2019-07-01
You could try a new version of [libratbag](https://github.com/libratbag/libratbag) with [piper](https://github.com/libratbag/piper) to configure your mouse. They say it's supported. There's a PPA that includes them both, but I don't know for sure that it works with 16.04: I've only used it with 18.04.

---

### Post by mydroog on 2019-07-03
> **CatKiller said:**
> You could try a new version of [libratbag]("https://github.com/libratbag/libratbag") with [piper]("https://github.com/libratbag/piper") to configure your mouse. They say it's supported. There's a PPA that includes them both, but I don't know for sure that it works with 16.04: I've only used it with 18.04.

So those two tools did not do anything for me. I did some more digging and made a bit of progress but still nothing much..

Using hcitool, I was actually able to discover the mouse:

```
sudo hcitool lescan
```

It comes up with the MAC address and name. When I attempt to use the LE connect command (sudo hcitool lecc "MAC ADDRESS", I always get an error.
Sometimes it says "Could not create connection: connection timed out" or "Could not create connection: Input/output error". No luck there

However, I was actually able to connect to the mouse using gatttool

```
sudo gatttool -t random -b MOUSEMACADDRESS -I
connect
```

The mouse is still completely unresponsive (IE cannot scroll, click, or anything really). But I am able to use gatttool to read characteristics from it and whatnot, however it seems that tool is just for reading information from a BT device and doesn't actually do anything useful.

I've also noticed after running hcitool lescan command, I can go through the applet and actually see the mouse .. but it also fails to pair.

Any ideas appreciated. Seems like ubuntu support for bluetooth mice is still horrendous

---

### Post by mydroog on 2019-07-03
New development:

I got into the file /etc/bluetooth/main.conf (using sudo nano)

I uncommented (removed the hashtag) of ControllerMode and changed it to ControllerMode = le.

After a reboot, the first thing that came up was a system error that gatttool crashed for some reason. The bluetooth applet showed it was off, when I turned it back on, I was able to use the wizard to detect, pair, and now am successfully using the mouse (Logitech MX Anywhere 2S) through bluetooth.

Does anyone have a suggestion for diagnosing why the system error shows up during boot? I messed around with so many settings, I believe I returned them all back to stock (Other than the controller mode mentioned above), but can't be sure. Perhaps that is what's causing the crash.

Edit: After another reboot, the above crash and respective request to report the error does not occur. Bluetooth still remains off after boot until I turn it back on from the applet. Mouse reconnects perfectly when BT is turned back on though.

---

### Post by nilandj-nilandsplace on 2019-07-30
I had a similar problem with Bluetooth over my wifi adapter card for Ubuntu-gmome 14.04. The old ateros card worked but the bluetooth co-existence was always poor. I had upgraded the wifi card and antennas to an Intel dual-AC 7260 card but could never get bluetooth to work in ununtu or win7 (-dual boot HP ProBook 440 G1). So the next Idea was to try a Broadcomm BCM4352 and I had the same problem.

After to weeks of chasing forms, links and support options I could not get my mouse to work!

In the terminal command line **$ bluetoothctl** it never would find the controller. **$ blueman-manager** would not work neither would **$ bluetooth-wizard.**
But then I ran **$ sudo bluetooth-wizard** and it found my mouse in less then a second. 
Some forums suggest it is a problem of permissions of RFcomm or hci0 but the answers are too convoluted and doing** $ sudo usermod -aG plugdev users wheel lp** did not seam to work and was an answer for slackware64 anyway.

Only **$ sudo bluetooth-wizard** worked!!!

[B]Note:
[/B]Ubuntu will INSTALL the Brodcomm firmware drivers for BMC4252 under aditional drvivers, ($ /usr/bin/software-properties-gtk --open-tab=4) but will not install the needed bluetooth firmware driver for BCM20702A1.
You will need to hack this yourself and add it as /lib/firmware/brcm/BCM.hcd or /lib/firmware/brcm/BCM20702A1-0a5c-21fb.hcd. The secret is the octal code found by doing $ spci -knn | grep Net -A3; lsusb in Mine it came up as:

03:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
Subsystem: Hewlett-Packard Company Device [xxx:xxxx]
Kernel driver in use: wl
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04f2:b3c8 Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 15d9:0a4e Trust International B.V. 
Bus 003 Device 004: ID 0a5c:21fb Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

...and the needed info is in the second to the last line "0a5c:21fb" that is the device and manufacturer code.
The hack was made from broadcom-sta-dkms_6.30.223.271-5_all.deb or windows DR_USB_BT400_1201710_Windows.zip, but you will need another program to convert the hex file to a .hcd file. The newer version did not work so I stuck with 6.30.223.271-5
I did a search for "Firmware for BCM20702A1 based devices" and found it. Don't expect to find it from Broadcomm as it seems they have hidden them, but I found them on a dell website.

Perhaps the Intel card would have worked if I had run **$ sudo bluetooth-wizard **as that card I did not need to do a hack for the drivers? Any one need some Intel PCIe half cards for a Laptop?
-James

---

