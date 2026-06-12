---
title: "lircd and mce usb IR transceiver"
date: 2016-09-02
forum: Hardware
---

### Post by jschwalbe on 2016-09-02
**EDITED: This posting can serve as a HOW-TO, because it works. I didn't think it was working, because the IR blaster was too far away. It basically had to be RIGHT NEXT TO the device it was to control. So there you go.**


Greetings. I'm sort of a Ubuntu newbie, so please bear with me. I've searched but haven't found a suitable forum posting that I can adapt to my problem.

I'm running 16.04 on an old(ish) Mac Mini.  I've got a HP MCE USB IR Transceiver device that I'd like to use to turn send IR signals to turn on/off projector and a receiver, etc.

So far it seems the device partially works.. but I need some help. I've been able to "record" some remote from the USB device. But I when I try to use ir-send, the IR blaster blinks a red light but doesn't control any of my devices. 

Upon plugging in the USB Transceiver -- dmesg:
```
[174812.112065] usb 3-1: new full-speed USB device number 4 using uhci_hcd[174812.282128] usb 3-1: New USB device found, idVendor=0471, idProduct=0815
[174812.282137] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[174812.282143] usb 3-1: Product: eHome Infrared Transceiver
[174812.282149] usb 3-1: Manufacturer: Philips
[174812.282154] usb 3-1: SerialNumber: PH00Zrpu
[174812.290135] Registered IR keymap rc-rc6-mce
[174812.290366] input: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/rc/rc0/input12
[174812.290578] rc0: Media Center Ed. eHome Infrared Remote Transceiver (0471:0815) as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/rc/rc0
[174812.290922] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input13
[174812.292259] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[174812.500088] mceusb 3-1:1.0: Registered Philips eHome Infrared Transceiver with mce emulator interface version 1
[174812.500098] mceusb 3-1:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x1 active)
```

dpkg-reconfigure lirc --> (selected these, but not sure if correct)
  Remote control configuration: Windows Media Center Transceivers/Remotes (all)                      
  IR transmitter, if present: Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box

When I do the following (and mash buttons on remotes):
```

ob1@epic:~$ sudo cat /dev/lirc0 
?"0X?X?X?XrX?X?X?X?X@?@X?X?XrX?X?X?X@?@XrX?X?X?X?X@??X?X?X@XrX@XrX?X???"X???^C

```


and mashing on remotes again:
```

ob1@epic:~$ sudo mode2 -d /dev/lirc0
space 16777215
pulse 9000
space 4350
pulse 650
. . .^C

```

ob1@epic:/tmp$ sudo irrecord --device /dev/lirc0 -f /tmp/ACER --disable-namespace

Which created a file:
```

begin remote


  name  /tmp/ACER
  flags RAW_CODES|CONST_LENGTH
  eps            30
  aeps          100


  gap          107209


      begin raw_codes


          name ASUS-POWER
             8950    4400     600     500     600     500
              600     500     600    1600     650     450
              650     500     600     500     600     500
              600    1600     650    1600     600     500
              600     500     600    1650     600     500
              600     500     600     500     600    1600
              650    1600     600    1600     650     500
              600     500     600     500     600     500
              600    1600     600     500     600     550
              600     500     600    1600     600    1650
              600    1600     600    1650     600     500
              600


      end raw_codes


end remote



```

ob1@epic:/tmp$ sudo cp ACER /etc/lirc/lircd.conf

**And here's the rub**:
```

ob1@epic:/tmp$ irsend SEND_ONCE /tmp/ACER ASUS-POWER

```

The IR blaster plugged into the back of this device flashes red once. The projector, however, does *nothing*. :( 

Where have I messed up? Anyone done this before?  

Thanks.

---

### Post by Bucky Ball on 2016-09-03
*Thread moved to **Apple Hardware Users**.*

---

### Post by jschwalbe on 2016-09-03
> **Bucky Ball said:**
> *Thread moved to **Apple Hardware Users**.*

Hi Bucky Ball - do you mind undoing that move? I don't see how this is related to it being on a Mac Hardware. My problem more so seems to be with the lirc software configuration and the USB device than anything else. I need as broad an audience as possible. Thanks Mods!

---

### Post by Bucky Ball on 2016-09-03
After staff discussion, moved back to ***Hardware***.

Good luck with it. :)

---

### Post by jschwalbe on 2016-09-04
Well turns out that the above is a good way to to it. The IR blaster I was using "blasts" about 2 cm away. So, it works. Feel free to use the above as a template to make it work, I guess.

---

