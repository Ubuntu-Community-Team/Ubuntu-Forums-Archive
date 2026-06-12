---
title: "Fiio e10k USB-DAC - L&amp;R audio channels reversed on 16.04"
date: 2016-05-04
forum: Hardware
---

### Post by bswarm2 on 2016-05-04
My Fiio e10k USB-DAC was working properly on Ubuntu 14.04, but when I did a fresh install of 16.04 the left and right audio channels are reversed. This is only a problem with the USB-DAC, the computers onboard audio has the correct left/right orientation. So, I need to swap channels on the USB-DAC, but leave the onboard audio the way is is.
Edit: I tried adding this to ~/.pulse/default.pa but there's 2 choices in sound settings for this device, an analog USB-DAC and a digital USB-DAC. It's only changing the the one named "analog", the "digital" one is still reversed.
```
load-module module-remap-sink sink_name=reverse-stereo master=1 channels=2 master_channel_map=front-right,front-left channel_map=front-left,front-right
set-default-sink reverse-stereo
```

```
$ arecord -l**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC3239 Analog [ALC3239 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: ALC3239 Alt Analog [ALC3239 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [DigiHug USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```
```
DigiHug USB AudioManufacturer: FiiO
Speed: 12Mb/s (full)
USB Version:  1.10
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 8
Number of Configurations: 1
Vendor Id: 1852
Product Id: 7022
Revision Number:  0.01


Config Number: 1
    Number of Interfaces: 4
    Attributes: 80
    MaxPower Needed: 500mA


    Interface Number: 0
        Name: usbhid
        Alternate Number: 0
        Class: 03(HID  ) 
        Sub Class: 00
        Protocol: 00
        Number of Endpoints: 1


            Endpoint Address: 81
            Direction: in
            Attribute: 3
            Type: Int.
            Max Packet Size: 18
            Interval: 32ms


    Interface Number: 1
        Name: snd-usb-audio
        Alternate Number: 0
        Class: 01(audio) 
        Sub Class: 01
        Protocol: 00
        Number of Endpoints: 0


    Interface Number: 2
        Name: snd-usb-audio
        Alternate Number: 0
        Class: 01(audio) 
        Sub Class: 02
        Protocol: 00
        Number of Endpoints: 0


    Interface Number: 2
        Name: snd-usb-audio
        Alternate Number: 1
        Class: 01(audio) 
        Sub Class: 02
        Protocol: 00
        Number of Endpoints: 1


            Endpoint Address: 82
            Direction: in
            Attribute: 9
            Type: Isoc
            Max Packet Size: 388
            Interval: 1ms


    Interface Number: 2
        Name: snd-usb-audio
        Alternate Number: 2
        Class: 01(audio) 
        Sub Class: 02
        Protocol: 00
        Number of Endpoints: 1


            Endpoint Address: 82
            Direction: in
            Attribute: 9
            Type: Isoc
            Max Packet Size: 582
            Interval: 1ms


    Interface Number: 3
        Name: snd-usb-audio
        Alternate Number: 0
        Class: 01(audio) 
        Sub Class: 02
        Protocol: 00
        Number of Endpoints: 0


    Interface Number: 3
        Name: snd-usb-audio
        Alternate Number: 1
        Class: 01(audio) 
        Sub Class: 02
        Protocol: 00
        Number of Endpoints: 1


            Endpoint Address: 03
            Direction: out
            Attribute: 9
            Type: Isoc
            Max Packet Size: 388
            Interval: 1ms


    Interface Number: 3
        Name: snd-usb-audio
        Alternate Number: 2
        Class: 01(audio) 
        Sub Class: 02
        Protocol: 00
        Number of Endpoints: 1


            Endpoint Address: 03
            Direction: out
            Attribute: 9
            Type: Isoc
            Max Packet Size: 582
            Interval: 1ms


    Interface Number: 3
        Name: snd-usb-audio
        Alternate Number: 3
        Class: 01(audio) 
        Sub Class: 02
        Protocol: 00
        Number of Endpoints: 1


            Endpoint Address: 03
            Direction: out
            Attribute: 9
            Type: Isoc
            Max Packet Size: 192
            Interval: 1ms
```

Edit: Solved... There was a new sound device listed as "Remapped Digihug USB Digital Stereo" at the very bottom of the sound settings after I added the code above. Didn't see it at first.

2nd Edit: Unsolved... The audio quality isn't what it should be. When going back to the default configuration and using VLC media players "reverse stereo" setting, the audio quality improves drastically. I really don't know where to go from here, it worked fine in Ubuntu 14.04.

---

### Post by bswarm2 on 2016-05-14
Bump?

---

### Post by bswarm2 on 2016-05-18
Bumping one more time. I need a system wide solution to get the stereo audio channels reversed. The solution above results in substandard audio quality. The only way that works so far is to use VLC and change the audio settings "reverse stereo" each time a different file is played, and I'd rather use Audacious. Again, this wasn't a problem with 14.04
[ATTACH=CONFIG]269148[/ATTACH]

---

