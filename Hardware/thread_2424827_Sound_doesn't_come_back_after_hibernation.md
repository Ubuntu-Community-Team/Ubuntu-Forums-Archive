---
title: "Sound doesn't come back after hibernation"
date: 2019-08-15
forum: Hardware
---

### Post by itAyXD on 2019-08-15
I tried to debug it myself and had some success, but still need some advice in order to solve the problem properly.
**The Problem**: After I put my computer to hibernation I have no sound (suspend works fine).
**My system**: HP spectre X360 4100 - Broadwell
**The error message**: dmesg shows ```
rt286 i2c-INT343A:00: I2C error -110
```

**The partial solution**:
I can get the sound back if I go to pavucontrol, switch to headset and then back to built-in speakers. But it's too loud, I have to open alsamixer, choose the card and lower the volume on master. That will bring the sound back to normal.

**The questions**:

[LIST=1]
[*]Anyone has an idea why this is happening based on the error message or the "solution"? 
[*]Anyone has a way to automate the "solution"? 
[*]Any other insights? 
[/LIST]


I'd be happy to supply any additional necessary info...


**Bonus:**
If I set ```
acpi_osi='!Windows 2013' acpi_osi='!Windows 2012'
``` on grub, the sound works, and keep working even after hibernation but then there is a problem with the accelerometer, and `monitor-sensor` reports it as "undefined". 
When I do that aplay gives different output for the card:
```
card 1: PCH [HDA Intel PCH], device 0: ALC3242 Analog [ALC3242 Analog]
```
might be a different approach to solving the problem, but I don't know enough about ACPI...
normal output from `aplay -l`:
```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: broadwellrt286 [broadwell-rt286], device 0: System Playback/Capture (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: broadwellrt286 [broadwell-rt286], device 1: Offload0 Playback (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: broadwellrt286 [broadwell-rt286], device 2: Offload1 Playback (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by joris_donders2 on 2019-08-16
when you adjust alsa it works ; but do you store your new settings in alsamixer?  

```
alsamixer store 
```

---

### Post by itAyXD on 2019-08-16
Well, adjusting alsa doesn't make it work, what makes it work is deselecting it and selecting it in pavucontrol. Only then I have to adjust it in alsa, but that itself doesn't get the sound back.
Anyway, I also tried to do `alsactl store`.
Thanks for your reply though.

---

### Post by joris_donders2 on 2019-08-16
[https://www.maketecheasier.com/fix-no-sound-issue-ubuntu/](https://www.maketecheasier.com/fix-no-sound-issue-ubuntu/)

and

[https://leimao.github.io/blog/Ubuntu-No-Sound-Fix/](https://leimao.github.io/blog/Ubuntu-No-Sound-Fix/)

could these tips provide a good solution for you ?

---

### Post by markackerman8@gmail.com on 2019-08-21
A possible 'messy' fix that works well on my system 9proving that Ubuntu DOES know how to suspend 'PROPERLY' ...

is to simply tell Ubuntu to "PAUSE", and when it does it will give ONLY one of two OPTIONS, Quit or Suspend, then Suspend works for me with the sound coming back on through the HDMI

Just a messy fix but works

Always Trying to Help, Mark :p

Good Luck, Mark

---

