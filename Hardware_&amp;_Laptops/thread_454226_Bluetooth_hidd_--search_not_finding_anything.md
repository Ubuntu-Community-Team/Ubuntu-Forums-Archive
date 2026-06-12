---
title: "Bluetooth: hidd --search not finding anything"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by rchille on 2007-05-25
Good morning all,

I just got a shiny new LG vx9900 cell phone with a Jabra BT8010 Head set. I decided to pair them with my docked laptop (running Feisty) via a Kensington 33348 USB Dongle.

With dreams of listening to my laptops ogg's, I started working through the forums to enable this.

Sadly, I hit a roadblock a few hours ago and cannot work past it. When I type:
```

hidd --search
Searching.....

```

"hidd scan" doesn't return anything.

And that is the end of it. Neither my phone nor headset detect. 

I'm working from this guide: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

"hcitool dev" gives me back:
```

Devices:
        hci0    00:16:38:3A:56:89

```

And "hciconfig -a" gives me:
```

hci0:   Type: USB
        BD Address: 00:16:38:3A:56:89 ACL MTU: 1017:8 SCO MTU: 64:8
        UP RUNNING PSCAN AUTH 
        RX bytes:5640 acl:0 sco:0 events:236 errors:0
        TX bytes:1113 acl:0 sco:0 commands:74 errors:0
        Features: 0xff 0xff 0x8d 0xfe 0x9b 0xfd 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'trimaxion-0'
        Class: 0x3e0100
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Uncategorized
        HCI Ver: 2.0 (0x3) HCI Rev: 0x2149 LMP Ver: 2.0 (0x3) LMP Subver: 0x415c
        Manufacturer: Broadcom Corporation (15)

```

I have tried the /etc/init.d/bluetooth restart a few times and have both my phone and headset in pairing mode.

Just for fun I also tried installing from synaptic. "Bluetooth File Sharing" and "Multisync" hoping they would install the magic config/piece that I'm missing. 

What else can I try? Is there any glaring config problem that ya'll can see??
Thanks in advance!

BTW: I have tried a few versions of ps -ef | grep (blue, BLUE, bt, ...) but haven't hit on the right combo to confirm my service is running.

---

### Post by rchille on 2007-05-25
Herre was my first problem:
> "hidd scan" doesn't return anything.

Apparently I shouldn't attempt anything with computers until after I've had 3 cups of coffee.
The command "hcitool scan" works beautifully and returns:

```

rob@trimaxion:~$ hcitool scan
Scanning ...
        00:16:CB:0D:BD:C3       John Doe&#8217;s Computer
        00:13:17:F4:5E:65       Jabra BT8010

```

The forum that I should have been using is here: [http://ubuntuforums.org/showthread.php?t=224673&highlight=bluetooth+keyboard](http://ubuntuforums.org/showthread.php?t=224673&highlight=bluetooth+keyboard)

---

### Post by rchille on 2007-05-25
Alright, I'm in the thick of it now!

When I issue a connect command I get this:
```
rob@trimaxion:/sbc/plugz# sudo hidd --connect 00:13:17:F4:5E:65
Can't get device information: Success
```

The "Can't get device info" worries me.

I followed the info on the bluetooth-alsa page but no luck. Everything seems to install okay, but the a2dpd doesn't show in xmms.

Ideas?

---

