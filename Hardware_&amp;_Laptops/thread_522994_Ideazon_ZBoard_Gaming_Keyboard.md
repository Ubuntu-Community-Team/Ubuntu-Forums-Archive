---
title: "Ideazon ZBoard Gaming Keyboard"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by dannystaple on 2007-08-11
I am talking about the gaming keyboard with interchangeable keys, not the other Ideazon keyboards (which I will not name so as not to spike the exclude search in Google).

I am trying to figure out how to make the mutlimedia keys work on this keyboard. Consider this a braindump, and if other people better versed in linux USB hardware drivers can use this info, then a driver that supports the extra keys (if one does not already exist which I cannot find) can be created.

I have actually had to dig pretty far down the USB system to get the information I have so far.

So starting with lsusb this is what I see for this keyboard:
```

Bus 002 Device 003: ID 1038:0100 Ideazon, Inc. Zboard
Bus 002 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-port Hub

```

The keyboard has two additional USB ports, which I will for the time being assume is the device shown as an  Atmel Corp. at43301 4-port Hub. I will therefore ignore that, and focus on the device at 002:003.

The keyboards multimedia keys do not produce scancodes, even when in raw. In fact they do not even produce interrupts, and cannot be seen with dmesg. 

I suspect that this is because the multimedia keys are actually on a separate interface and endpoint. When examining /proc/bus/usb/devices for the keyboard - this is what I see:

```
T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=01 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1038 ProdID=0100 Rev=10.98
S:  Manufacturer=Ideazon
S:  Product=Zboard
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```

Examining this output, there are clearly 2 "I" lines, with an "E" line for each. The first, using the usbhid driver, must be the normal 105 key keyboard. I suspect we can ignore this, but I will dig deeper:
```

# lsusb -v -s 002:003
Bus 002 Device 003: ID 1038:0100 Ideazon, Inc. Zboard
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1038 Ideazon, Inc.
  idProduct          0x0100 Zboard
  bcdDevice           10.98
  iManufacturer           1 Ideazon
  iProduct                2 Zboard
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          4 HID Keyboard
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              5 EP1 Int
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      64
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              6 EP2 Int
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     108
          Report Descriptor: (length is 108)
            Item(Global): Usage Page, data= [ 0x0c ] 12
                            Consumer
            Item(Local ): Usage, data= [ 0x01 ] 1
                            Consumer Control
            Item(Main  ): Collection, data= [ 0x01 ] 1
                            Application
            Item(Global): Logical Minimum, data= [ 0x00 ] 0
            Item(Global): Logical Maximum, data= [ 0x01 ] 1
            Item(Global): Report Size, data= [ 0x01 ] 1
            Item(Global): Report Count, data= [ 0x01 ] 1
            Item(Local ): Usage, data= [ 0xb8 ] 184
                            Eject
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0xe9 ] 233
                            Volume Increment
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0xea ] 234
                            Volume Decrement
            Item(Main  ): Input, data= [ 0x02 ] 2
                            Data Variable Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0xe2 ] 226
                            Mute
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0xcd ] 205
                            Play/Pause
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0xb5 ] 181
                            Scan Next Track
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0xb6 ] 182
                            Scan Previous Track
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x94 0x01 ] 404
                            AL Local Machine Browser
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x92 0x01 ] 402
                            AL Calculator
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0xb7 ] 183
                            Stop
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x96 0x01 ] 406
                            AL Internet Browser
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x8a 0x01 ] 394
                            AL Email Reader
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x85 0x01 ] 389
                            AL Text Editor
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x99 0x01 ] 409
                            AL Network Chat
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x1f 0x02 ] 543
                            AC Find
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x8b 0x01 ] 395
                            AL Newsreader
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Local ): Usage, data= [ 0x81 0x01 ] 385
                            AL Launch Button Configuration Tool
            Item(Main  ): Input, data= [ 0x06 ] 6
                            Data Variable Relative No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report Size, data= [ 0x2f ] 47
            Item(Main  ): Input, data= [ 0x01 ] 1
                            Constant Array Absolute No_Wrap Linear
                            Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Global): Report Size, data= [ 0x01 ] 1
            Item(Global): Usage Page, data= [ 0x08 ] 8
                            LEDs
            Item(Local ): Usage, data= [ 0x4b ] 75
                            Generic Indicator
            Item(Global): Report Size, data= [ 0x01 ] 1
            Item(Global): Report Count, data= [ 0x40 ] 64
            Item(Main  ): Output, data= [ 0x20 ] 32
                            Data Array Absolute No_Wrap Linear
                            No_Preferred_State No_Null_Position Non_Volatile Bitfield
            Item(Main  ): End Collection, data=none
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
Device Status:     0x0002
  (Bus Powered)
  Remote Wakeup Enabled

```

Now this was pretty conclusive. The second interface has a human interface class and even better, shows each multimedia key as a named item. I now have to dig a bit deeper into how USB stuff works to get more on how to use these items.

I have already had the usbmon module loaded, and checked /sys/kernel/debug/usbmon, but not been able to really understand what is going on there. I am reading around a few sites to figure this out, and a few years ago bought Jan Axelson's USB Complete which may help too.

Sites I am looking at:
[LIST]
[*][Programming Guide for Linux USB Device Drivers]("http://www.usbman.com/linuxusb.htm")
[*][http://www.quietearth.us/articles/2006/10/16/USB-Snoop-in-linux]("http://www.quietearth.us/articles/2006/10/16/USB-Snoop-in-linux") - Much of this is not actually necessary, as Feisty already has the USBMON present, and you only need to mount the debug filesystem then load the module, no need to compile the kernel.
The other tool referred to by this site has been largely useless - in that I have not successfully got it to compile and run in any useful way.
[*][USB Keyboard: Missing Scancodes- KernelTrap]("http://kerneltrap.org/node/6460") - This thread has a different keyboard, but led me to trying lsusb -v to get more info.
[/LIST]

I am going to carry on working on it and update the thread as I get further into this. Please let me know if you have got this work, or are able to help in getting this to work. Note again - this is the Zboard Gaming keyboard with changeable keys, not any of the other Ideazon zboard products.

Cheers,
Danny

---

### Post by Yellow Onion on 2007-08-14
I have The same thing Been trying to get it to work for awhile from what i found is the USB drivers for keyboard doesn't work with multimedia keys (on any or most keyboards) so your on the right path also found some software called soft touch i think but cant remember the name exactly but the author was also working on a more universal driver too

---

### Post by Skarn on 2007-11-09
I have a Zboard... I'm still using a dual boot Kubuntu - XP system for gaming but i'd like to make my multimedia buttons work... did the two of you give up?
Any updates?
I'm not a great expert, but I'd like to be of help in any way I can.

---

### Post by nzadLithium on 2008-01-06
I'm using gutsy dual boot with xp. I notice that it says max power 100mA but on the back of the zboard it says ps/2 version is 300mA and usb version (which is the one i have) is 500mA. 

Everywhere i look on the net there is so much info about getting a merc going. Where is the info on getting a standard zboard going? The gaming keypad works great on this :D (work without having to play around with anything) but the multimedia keys do not give any events in xev :S

Anyone gots any ideas at all?

---

### Post by Skarn on 2008-01-07
I think dannystaple is the single person who obtained more information on the ZBoard at least from what I have been able to read on the internet.

If I have caught the point, there is not one, but two keyboard inside a ZBoard, but while  one is a standard qwerty keyboard, we currently don't have a working available driver for the other one.
Still it is recognized by the OS as an input device...

Said this, I don't possess the capabilities required to solve this problem (n00b).
From what (very little) I understood this sounds like something relatively easy for somebody who knows where to put his hands...

---

### Post by Dandeloreon on 2008-05-09
I can addd a little bit more to this... namely some of the keypress codes that i got

after i got that i did go and attempt to get a few key codes from the device... the main keys i found where on interface 1... here's what i got from usbmon: ( note that for this test, my zboard was located on bus 1 and as device number 6.

```

volume down:
f7fb6e80 3031247883 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3031247907 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3031367889 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3031367911 S Ii:1:006:1 -115:8 8 <
volume up:
f7fb6e80 3072650260 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3072650277 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3072730264 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3072730287 S Ii:1:006:1 -115:8 8 <
mute:
f7fb6e80 3113108583 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3113108605 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3118084866 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3118084885 S Ii:1:006:1 -115:8 8 <
prev:
f7fb6e80 3323816675 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3323816700 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3324128693 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3324128719 S Ii:1:006:1 -115:8 8 <
stop:
f7fb6e80 3340465630 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3340465649 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3340673643 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3340673666 S Ii:1:006:1 -115:8 8 <
play:
f7fb6e80 3353586384 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3353586404 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3353738392 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3353738413 S Ii:1:006:1 -115:8 8 <
next:
f7fb6e80 3369227281 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3369227302 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3369507297 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3369507318 S Ii:1:006:1 -115:8 8 <
special 1:
f7fb6e80 3383148080 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3383148099 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3383316090 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3383316108 S Ii:1:006:1 -115:8 8 <
special 2: ( My documents ? )
f7fb6e80 3399685030 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3399685058 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3399861039 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3399861063 S Ii:1:006:1 -115:8 8 <
special 3: ( calculator )
f7fb6e80 3406821439 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3406821465 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3406981449 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3406981478 S Ii:1:006:1 -115:8 8 <
special 4: ( Word? )
f7fb6e80 3433566974 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3433566998 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3433710982 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3433711004 S Ii:1:006:1 -115:8 8 <
special 5: ( Instant messenger )
f7fb6e80 3444319591 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3444319617 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3444455599 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3444455624 S Ii:1:006:1 -115:8 8 <
special 6: ( Email )
f7fb6e80 3457912371 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3457912393 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3458184386 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3458184410 S Ii:1:006:1 -115:8 8 <
special 7: (search)
f7fb6e80 3487746084 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3487746108 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3487890093 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3487890120 S Ii:1:006:1 -115:8 8 <
special 8: (www/IE)
f7fb6e80 3505971130 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3505971149 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3506107136 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3506107156 S Ii:1:006:1 -115:8 8 <
special 9: ( ideazon.com? )
f7fb6e80 3519267892 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3519267913 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3519411901 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3519411920 S Ii:1:006:1 -115:8 8 <
zboard key:
f7fb6e80 3548477568 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3548477579 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3548573571 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3548573580 S Ii:1:006:1 -115:8 8 <
bar lock:
f7fb6e80 3589271909 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3589271930 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3589423915 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3589423931 S Ii:1:006:1 -115:8 8 <
key tips:
7fb6e80 3603592732 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3603592760 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3603704739 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3603704763 S Ii:1:006:1 -115:8 8 <
pad lock:
f7fb6e80 3622353809 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3622353831 S Ii:1:006:1 -115:8 8 <
f7fb6e80 3622465815 C Ii:1:006:1 0:8 8 = 00000000 00000000
f7fb6e80 3622465834 S Ii:1:006:1 -115:8 8 <

```

---

