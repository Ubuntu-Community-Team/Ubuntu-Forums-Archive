---
title: "Cant get any sound due to lack of support of my audio chain, any help / solutions?"
date: 2016-07-08
forum: Hardware
---

### Post by infernouk on 2016-07-08
Hey guys

Just installed Ubuntu to give it a go. But im having an issue that means I cant get any sound.

I run a thunderbolt card which plugs into my motherboard, this has drivers for windows only. 

I then use a thunderbolt to firewire dongle from apple to make it firewire.

Then i plug my firewire interface into the adapter, this device also only has mac or windows drivers.

So basically, am i screwed because there are no linux drivers for these components? 

I assume the only way around is to invest in a class compliant audio interface? 

Cheers for any help here as I cant really use the OS if there is no sound!

---

### Post by Bucky Ball on 2016-07-08
Welcome. Have you tried a hunt for 'ubuntu firewire' or '[ubuntu thunderbolt]("https://duckduckgo.com/?q=Ubuntu+thunderbolt&t=ha&ia=web")' or 'ubuntu <name-of-your-outboard-device-here>'? Might shed some light. And [both of them together looks even more promising]("https://duckduckgo.com/?q=Ubuntu+thunderbolt+to+firewire&t=ha&ia=web"). 

Screwed? Probably not. I have no experience with using Thunderbolt but sure there are others that do. I do have experience with Firewire and know that works fine. In the meantime, could you provide a couple more bits of pertinent info, please. 

Name of outboard audio device
Release and flavour of Ubuntu (Ubuntu Studio 14.04 for example)

Perhaps start with testing the chain. With nothing plugged in to the thunderbolt/firewire port does Ubuntu see the thunderbolt card is there? If so, move on. Plug in the device and open a terminal and run this immediately:

```
dmesg
```

Near the bottom you should see an acknowledgement that the device was plugged in and whether it was configured and other useful info. If not, back to the drawing board. But if thunderbolt is seen and device is not, probably concentrate on Firewire device.

Also if not, and you know Ubuntu is seeing the thunderbolt card and firewire, post the output of that last bit of the dmesg between code tags, please (see link in my signature for code tags).

PS: Also, what is making you suspect it is not working now? You mention '... then I plug my device in' then you can't get any sound. What are you doing to find it? Do you suspect Ubuntu is not seeing the Thunderbolt card or the adapter? How are you detecting that Ubuntu is not recognising the Firewire device? Because you can't see it?

You might try tweaking Pulseaudio Volume Control. Not sure if that's installed in Ubuntu by default but it is in the repos (Ubuntu Software or Gnome? Not certain what's being used now). ;)

---

### Post by infernouk on 2016-07-08
> **Bucky Ball said:**
> Welcome. Have you tried a hunt for 'ubuntu firewire' or '[ubuntu thunderbolt]("https://duckduckgo.com/?q=Ubuntu+thunderbolt&t=ha&ia=web")' or 'ubuntu <name-of-your-outboard-device-here>'? Might shed some light. And [both of them together looks even more promising]("https://duckduckgo.com/?q=Ubuntu+thunderbolt+to+firewire&t=ha&ia=web"). 

Screwed? Probably not. I have no experience with using Thunderbolt but sure there are others that do. I do have experience with Firewire and know that works fine. In the meantime, could you provide a couple more bits of pertinent info, please. 

Name of outboard audio device
Release and flavour of Ubuntu (Ubuntu Studio 14.04 for example)

Perhaps start with testing the chain. With nothing plugged in to the thunderbolt/firewire port does Ubuntu see the thunderbolt card is there? If so, move on. Plug in the device and open a terminal and run this immediately:

```
dmesg
```

Near the bottom you should see an acknowledgement that the device was plugged in and whether it was configured and other useful info. If not, back to the drawing board. But if thunderbolt is seen and device is not, probably concentrate on Firewire device.

Also if not, and you know Ubuntu is seeing the thunderbolt card and firewire, post the output of that last bit of the dmesg between code tags, please (see link in my signature for code tags).

PS: Also, what is making you suspect it is not working now? You mention '... then I plug my device in' then you can't get any sound. What are you doing to find it? Do you suspect Ubuntu is not seeing the Thunderbolt card or the adapter? How are you detecting that Ubuntu is not recognising the Firewire device? Because you can't see it?

You might try tweaking Pulseaudio Volume Control. Not sure if that's installed in Ubuntu by default but it is in the repos (Ubuntu Software or Gnome? Not certain what's being used now). ;)

Hi thanks for the response, ill try and provide what i can to help, firstly:
[COLOR=#000000]
[/COLOR]1. Im using a Steinberg MR816x Audio Interface 
[COLOR=#000000][/COLOR]
[COLOR=#000000]2. Im using the latest of the standard Ubuntu, 16.04?

[/COLOR]I am not seeing any mention of 'Thunderbolt' specifically in the console, here is a chunk of the bottom, hopefully enough:

```

[   11.385996] snd_hda_codec_hdmi hdaudioC1D0: HDMI: invalid ELD data byte 4[   11.528809] usb 3-9.2: New USB device found, idVendor=046d, idProduct=082d
[   11.528811] usb 3-9.2: New USB device strings: Mfr=0, Product=2, SerialNumber=1
[   11.528812] usb 3-9.2: Product: HD Pro Webcam C920
[   11.528813] usb 3-9.2: SerialNumber: 125A091F
[   11.606227] usb 3-9.3: new full-speed USB device number 6 using xhci_hcd
[   11.694254] usb 3-9.3: device descriptor read/64, error -32
[   11.886206] usb 3-9.3: device descriptor read/64, error -32
[   12.078240] usb 3-9.3: new full-speed USB device number 7 using xhci_hcd
[   12.154273] usb 3-9.3: device descriptor read/64, error -32
[   12.346275] usb 3-9.3: device descriptor read/64, error -32
[   12.538179] usb 3-9.3: new high-speed USB device number 8 using xhci_hcd
[   12.555959] usb 3-9.3: New USB device found, idVendor=2109, idProduct=2812
[   12.555961] usb 3-9.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   12.555962] usb 3-9.3: Product: USB2.0 Hub             
[   12.555963] usb 3-9.3: Manufacturer: VIA Labs, Inc.         
[   12.556379] hub 3-9.3:1.0: USB hub found
[   12.556736] hub 3-9.3:1.0: 4 ports detected
[   12.570424] media: Linux media interface: v0.10
[   12.575132] Linux video capture interface: v2.00
[   12.749544] usbcore: registered new interface driver snd-usb-audio
[   12.749549] uvcvideo: Found UVC 1.00 device HD Pro Webcam C920 (046d:082d)
[   12.749896] input: HD Pro Webcam C920 as /devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9.2/3-9.2:1.0/input/input21
[   12.749955] usbcore: registered new interface driver uvcvideo
[   12.749956] USB Video Class driver (1.1.1)
[   12.846184] usb 3-9.3.4: new high-speed USB device number 9 using xhci_hcd
[   12.947579] usb 3-9.3.4: New USB device found, idVendor=2109, idProduct=2812
[   12.947583] usb 3-9.3.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   12.947585] usb 3-9.3.4: Product: USB2.0 Hub             
[   12.947587] usb 3-9.3.4: Manufacturer: VIA Labs, Inc.         
[   12.947970] hub 3-9.3.4:1.0: USB hub found
[   12.948076] hub 3-9.3.4:1.0: 4 ports detected
[   13.911958] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   13.911990] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[   15.450240] usb 3-9.2: reset high-speed USB device number 5 using xhci_hcd

```

And i am assuming as ubuntu isnt seeing the thunderbolt card and hence isnt seeing the firewire device either, though i suspect even if it did see the card it wouldnt see the firewire device due to lacking drivers there as well

---

### Post by Bucky Ball on 2016-07-09
You *may* need drivers for the device. You don't need drivers for Firewire (or possibly Thunderbolt either) as they should be in the 16.04 kernel, and it seems you are a bit unclear where you need the drivers, which is understandable if you are direct from Windows. 

The driver installing merry-go-round undertaken in Win is generally not necessary in Ubuntu for many devices, at least for USB, Firewire, hotpluggables, and probably Thunderbolt. Looking around it seems others have Thunderbolt working without issue so there is nothing stopping you, theoretically, from getting this working. 

Try this:

> sudo lshw -C firewire

I've never tried that command with firewire, but give it a go with the device plugged in and post the output, if there is any.

I'm presuming the output in your last dmesg was directly after you plugged your device in and you did nothing in between then and running the 'dmesg' command?

Once again, open Pulseaudio Volume Control. Do you see the Steinberg when it's plugged in? Look in the drop down lists in Input and Output devices and also check the Configuration tab.

Not sure if you want to shorten your title a bit (Edit Post> Go Advanced) as doubt this is because of a 'lack of support for your audio chain'. Probably our lack of knowing how to connect it at this point, but hopefully we'll get there eventually. You are chatting with someone who doesn't use Thunderbolt or Firewire at the moment. If someone spots this that does it may be fixed in five or ten mins. :)

---

