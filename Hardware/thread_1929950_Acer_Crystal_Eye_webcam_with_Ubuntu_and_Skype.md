---
title: "Acer Crystal Eye webcam with Ubuntu and Skype?"
date: 2012-02-22
forum: Hardware
---

### Post by Josh Maxwell on 2012-02-22
Hey guys. I'm BRAND new to Ubuntu. My Acer Aspire 6920 laptop flatlined so a friend revived it by installing Ubuntu (not sure why he used it, but whatever, I like it so far. Also not sure what version of Ubuntu).

I just installed Skype 2.2 beta but it won't connect with my mic or Crystal Eye webcam and I have no clue where to start on fixing this. How do I get this to work?

Thanks! If any more info is needed please let me know.

---

### Post by scheibenlosen on 2012-02-24
> **Josh Maxwell said:**
> Hey guys. I'm BRAND new to Ubuntu. My Acer Aspire 6920 laptop fla tlined so a friend revived it by installing Ubuntu (not sure why he used it, but whatever, I like it so far. Also not sure what version of Ubuntu).

I just installed Skype 2.2 beta but it won't connect with my mic or Crystal Eye webcam and I have no clue where to start on fixing this. How do I get this to work?

Thanks! If any more info is needed please let me know.

With my Acer Aspire 4530, the mic works okay, but the camera doesn't no matter what program I use. I've tried it with Ubuntu 10.04.4, 11.10 and an Ubuntu-based distribution. It used to but, for some reason, has quit even though it shows up as the camera in the programs. I forget what I used to find out this information, but the app shows the camera listed as a keyboard. Go figger.

---

### Post by Jonam on 2012-03-01
I hadn't used Skype for a while but started to use it again and found that my Crystaleye webcam on my Acer AspireOne fails soon after starting. I get a few seconds of video and then it freezes. The same problem occurs in Ubuntu (9.04) or in Windows. Both OSs say that the USB hub cannot handle the speed of the camera and then disconnect the camera.

Printing dmesg gives the following information:

[  490.067841] usb 1-5: USB disconnect, address 2
[  490.328126] usb 1-5: new high speed USB device using ehci_hcd and address 3
[  490.396357] hub 1-0:1.0: unable to enumerate USB device on port 5
[  490.664134] usb 4-1: new full speed USB device using uhci_hcd and address 2
[  490.842299] usb 4-1: not running at top speed; connect to a high speed hub
[  491.047196] usb 4-1: configuration #1 chosen from 1 choice
[  491.050975] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (064e:d101)
[  491.055660] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input10

I have no idea why the camera no longer works when it used to work fine a while back. I am also unable to get either the internal or external mic working (lots of noise and no audio) in Ubuntu though it works fine under Windows.

I am at a complete loss as to why this is happening, I can only assume a hardware fault though this seems strange seeing that the camera does work for a while before failing.

Any suggestions as to what is wrong would help.

---

