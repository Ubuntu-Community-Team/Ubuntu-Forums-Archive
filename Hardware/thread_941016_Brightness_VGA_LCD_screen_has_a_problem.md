---
title: "Brightness VGA LCD screen has a problem"
date: 2008-10-07
forum: Hardware
---

### Post by V_jeroen on 2008-10-07
I Have a BTO laptop, my brightness fn shortcut works.
I can see the image on the screen that adds or reduces brightness.
But the brightness is not changing at all only in the file /proc/acpi/video/VGA0/DD03/brightness the value is changing.

Then if i log apci this is the output:
 ```
[Tue Oct  7 23:01:21 2008] received event "video DD03 00000086 00000000"
[Tue Oct  7 23:01:21 2008] notifying client 5594[107:116]
[Tue Oct  7 23:01:21 2008] notifying client 5777[0:0]
[Tue Oct  7 23:01:21 2008] notifying client 5777[0:0]
[Tue Oct  7 23:01:21 2008] executing action "/etc/acpi/video_brightnessup.sh"
[Tue Oct  7 23:01:21 2008] BEGIN HANDLER MESSAGES
grep: /proc/acpi/video/VGA/LCD/brightness: No such file or directory
/etc/acpi/video_brightnessup.sh: line 33: /proc/acpi/video/VGA/LCD/brightness: No such file or directory
[Tue Oct  7 23:01:21 2008] END HANDLER MESSAGES
[Tue Oct  7 23:01:21 2008] action exited with status 1
[Tue Oct  7 23:01:21 2008] completed event "video DD03 00000086 00000000"

```

So He cannot find the file VGA because it's in VGA0 ?
Is there something wrong with my drivers of the LCD screen?
My video card is an NVIDIA 8600 GTS card but I don't think that this has something to do with my problem. NVIDIA accelerated graphics driver is installed. System is ubunty 8.04


Does somebody has info or a workaround or sulotion for this problem ?

Thanx

Jeroen

---

