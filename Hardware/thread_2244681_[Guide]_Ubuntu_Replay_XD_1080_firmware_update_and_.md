---
title: "[Guide] Ubuntu Replay XD 1080 firmware update and live USB view"
date: 2014-09-18
forum: Hardware
---

### Post by djhedges on 2014-09-18
I recently purchased a Replay XD 1080 mini which is one of those action cameras like a Go Pro.  I just figured how to connect the camera to my laptop so I could see what the camera sees as I'm mounting it in the car and wanted to share in case anyone else is trying to get there camera working.  Or in case I forget what I did in the future. :confused:

First I did a firmware upgrade roughly following this [guide]("https://www.replay-xd.com.au/support/firmware-update/1080-mini-firmware-single-update/") from Replay XD.
As with most firmware updates there's a warning that interrupting the update while it's in progress could brick your camera.
[LIST=1]
[*]Insert a SD card into your laptop/desktop.
[*][Download Firmware]("http://www.replayxd.com/downloads/firmware/1080Mini/v1-3/XD1080miniFW_single_update_v1-3.zip")
[*]unzip ~/Downloads/XD1080miniFW_single_update_v1-3.zip -d /tmp/firmware
[*]cp /tmp/firmware/XD1080miniFW.bin /media/`whoami`/REPLAY\ XD
[*]umount /media/`whoami`/REPLAY\ XD
[*]Remove SD card and insert into the camera
[*]Connect via a USB cable.
[*]My camera was configured to auto start when given power.  If yours isn't power yet, power it on now.  The blue light will flicker really fast indicating the firmware is updating.  When it's finished it'll power off.
[*]Remove SD card
[*]Insert SD card back into laptop/desktop.
[*]rm /media/`whoami`/REPLAY\ XD/XD1080miniFW.bin  # If you don't remove this file your camera will always try to update the firmware.
[/LIST]

Now comes the easy part of using the camera like a webcam.
[LIST]
[*]touch /media/`whoami`/REPLAY\ XD/USB_LIVEVIEW.txt
[*]umount /media/`whoami`/REPLAY\ XD
[*]Insert the SD card into camera.
[*]Connect camera to laptop.  If it powers on automatically power it off.
[*]sudo apt-get install vlc
[*]Hold the record and power button on but don't release any buttons until the 4th vibration.  Only the blue light will be present when it's in the live USB camera mode.  I explicitly press the record and then the power, not sure if it matters.
[*]vlc  # Start VLC
[*]Media > Open Capture Device  # Clicky, clicky.  Sorry I don't know a fancy way to do this from a terminal and I'm to lazy to dig through the man pages.
[*]Set video device name to /dev/video1  # Check the drop down, it varies depending on the number of cameras you have.
[/LIST]

I'm digging the camera so far but haven't had a chance to really try it out yet.  Some neat features
[LIST]
[*][Settings]("http://replayxd.com/replay-xd1080-advanced/") are configured with a config file!
[*]12v wire kit.  I'm mounting this in a car and I can't tell you how many times I've been strapped in and forgot to turn on the Go Pro.  Or the Go Pro died, or the Go Pro ate itself, etc etc.
[*]Clobbers oldest videos first when space is low.
[/LIST]

It's worth mentioning the field of view on the camera is limited to 120 degrees which is less than the Go Pro.  Time will tell if I like or dislike this limit.
[http://replayxd.com/cameras/replay-xd-1080-mini/](http://replayxd.com/cameras/replay-xd-1080-mini/)

[ATTACH=CONFIG]256513[/ATTACH]

---

