---
title: "Headset not available as audio device sometimes"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by slowtrain on 2007-12-04
Yesterday, I had no problem plugging in and using my Plantronics headset (DSP 400).  Today, I can't get the headset to appear in the volume control or in sound preferences (it's not listed as a device).  I've tried rebooting, but the problem remains.  Since yesterday, I have added a bit of software to the computer, particularly a RPN calculator and GPG, but nothing sound related.

I've placed some relevant terminal output below.  It looks like the system 'sees' the headset when it is plugged in, but cannot turn it into an audio card because of some kind of error (cannot find the slot for index 0, error: -16).  Any suggestions would be welcome!

Cheers, Slowtrain

> 
From dmesg:
[ 2673.605169] usb 2-4: new full speed USB device using ohci_hcd and address 5
[ 2673.697811] usb 2-4: configuration #1 chosen from 1 choice
[ 2673.698705] cannot find the slot for index 0 (range 0-0), error: -16
[ 2673.698711] cannot create card instance 0
[ 2673.698716] snd-usb-audio: probe of 2-4:1.0 failed with error -5
[ 2673.702326] input: Plantronics Plantronics Headset as /class/input/input8
[ 2673.702350] input: USB HID v1.00 Device [Plantronics Plantronics Headset] on usb-0000:00:13.1-4

/etc/apt$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

/etc/apt$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 047f:0ca1 Plantronics, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 001: ID 0000:0000  


---

### Post by slowtrain on 2007-12-04
I should mention I'm running Gutsy on an AMD64 X2 (dual processor).

---

### Post by slowtrain on 2007-12-04
Rebooted again, this time with headphones plugged into a different USB port (possibly the one I was using earlier).  Now I have no problem accessing the headphones as an audio device.  Would love to know what could explain this.  Thoughts?

---

### Post by slowtrain on 2007-12-05
Ok, I take that back.  It's not the different usb port.  The port that previously was not working is now, after the 2nd reboot, working just fine.  dmesg doesn't include the 'cannot find the slot' and 'cannot create card instance' lines like before.  Looks to me like some kind of basic instability.  I read somewhere that compiling alsa into the kernel should reduce alsa instability.  I wonder if that would be worth the trouble?

---

### Post by slowtrain on 2007-12-15
Just an update on this problem.  I've had an opportunity not to see what happens over many operating system boots.  On most boots, the headsets are not recognized as a sound card, w/ dmesg giving the error above.  On a few boots, the error does not occur and I can use my headset.  I've also tried the Plantronics DSP 400 headset, which runs into the same problem--recognized some of the time.  I have no problem using these headsets on either OS X or Windows.  Evidently, something is wrong with the Ubuntu software.  If anyone has had luck addressing this problem, I'm all ears :) .  I'll look into reporting this to bugzilla, but will have to check if this is the kind of problem that gets reported there.


Cheers, Slowtrain

---

