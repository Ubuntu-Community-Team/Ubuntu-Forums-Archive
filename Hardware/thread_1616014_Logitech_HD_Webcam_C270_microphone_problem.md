---
title: "Logitech HD Webcam C270 microphone problem"
date: 2010-11-07
forum: Hardware
---

### Post by rofed69 on 2010-11-07
I am running Ubuntu 10.10 on a Sony VGN-AR71S and using the C270 webcam. The video works great but Skype doesn't recognise the microphone and the only option on the sound devices panel is the Pulse Audio server (local). The same goes for the laptop's built-in camera, but that is why I chose the Ubuntu-compatible C270.

---

### Post by c.webster on 2010-11-28
I've just bought a Logitech c270 webcam and I've got the same problem - no audio.  Can anyone suggest an idiot's guide way to fix it?

---

### Post by Njobristow on 2010-11-28
You need to go to System > Preferences > Sound, select the 'Input' tab and choose '0825 Analog Mono' (I also had to unmute it and adjust the 'Input volume'). In Skype it stays as the 'Pulse audio server'.

That worked for me and I've just had a long skype call using the C270. I'm not sure if the change is sticky though, or if you might have to reselect it if you unplug the camera / microphone.

Hope that helps,

Nick

P.S. I am on 10.10 so I can't vouch for earlier versions

---

### Post by c.webster on 2010-11-29
Yay!  That works for me.  Cheers

---

### Post by phorgan1 on 2011-02-15
I have the same problem, but the hardware for the audio is not recognized, so I can not go to configure the device.  It doesn't exist.  From dmesg after connecting:

```
[420740.288084] usb 2-4: new high speed USB device using ehci_hcd and address 5
[420740.637295] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0825)
[420740.733957] input: UVC Camera (046d:0825) as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input14

```

from lsusb:
```
Bus 002 Device 005: ID 046d:0825 Logitech, Inc. 

```
Anyone have any ideas?  I'd love for my C270 to have audio.

---

### Post by phorgan1 on 2011-02-15
All I had to do is sudo modprobe snd_usb_audio and the right device appeared.  After that I had to unmute it and select it for the software I was using, yay!

---

### Post by petalotis on 2012-04-06
> **Njobristow said:**
> You need to go to System > Preferences > Sound, select the 'Input' tab and choose '0825 Analog Mono' (I also had to unmute it and adjust the 'Input volume'). In Skype it stays as the 'Pulse audio server'.

That worked for me and I've just had a long skype call using the C270. I'm not sure if the change is sticky though, or if you might have to reselect it if you unplug the camera / microphone.

Hope that helps,

Nick

P.S. I am on 10.10 so I can't vouch for earlier versions

works for me thanks

---

### Post by brycenesbitt on 2012-08-31
The above solution also works for this device ID:
Bus 002 Device 002: ID 046d:081a Logitech, Inc.

---

