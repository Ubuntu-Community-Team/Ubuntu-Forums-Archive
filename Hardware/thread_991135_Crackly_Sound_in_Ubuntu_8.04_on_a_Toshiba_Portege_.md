---
title: "Crackly Sound in Ubuntu 8.04 on a Toshiba Portege 4010"
date: 2008-11-23
forum: Hardware
---

### Post by antandrades on 2008-11-23
hi all,

i am very new to ubuntu and linux. but i am enjoying learning the new os, and generally it's great.

i have one problem on my machine (Toshiba Portege 4010) though. Every time I play a song, or when the machine opens my account after logging in it crackles horribly.

i notice it also crackles when the hardware (an ALI soundcard) becomes active on boot up.

Anyone got any ideas or suggestions how to fix it?

thanks
ant

---

### Post by Jorge_C on 2008-11-24
Hi, we'll need some more info, can you please open a terminal (Applications -> Accessories) and paste the output of these commands here:
```
aplay -l
```
```
lspci -v | grep -i audio
```
and
```
cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by antandrades on 2009-01-05
Hi Jorge,

Thanks for getting back to me.

Here is the output you asked to see.

ant@ant-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: A5451 [ALI 5451], device 0: ALI 5451 [ALI 5451]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: A5451 [ALI 5451], device 1: ALI 5451 modem [ALI 5451 modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ant@ant-laptop:~$ lspci -v | grep -i audio
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
ant@ant-laptop:~$ 

ant@ant-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
ant@ant-laptop:~$ 

Happy new year btw :P

---

### Post by Jorge_C on 2009-01-29
Hi again, and sorry for taking so long to answer you. I googled a bit and found two threads that may be helpful for you.

In [this one]("http://ubuntuforums.org/showthread.php?t=27267") there is a fix that worked for an old ubuntu version, and it may still work.

In [this thread]("http://ubuntuforums.org/showthread.php?t=136179") you can find a different solution in the latest post.

I hope this helps, and feel free to ask if you have any doubts.

---

### Post by dave0109 on 2009-01-31
I too had crackly sound from the speakers on my Dell, although I'm running Ubuntu 8.10. Devices were picked up OK, my difference to you is that I have codecs listed...

```
cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9200
Codec: Conexant ID 2bfa
```

Much messing around later, I managed to fix it through the volume control UI.  Next to the date on the launcher panel, is the speaker icon.  Right mouse click and choose "Open Volume Control", in my case I had a single sound level slider for the "Master" volume.  I clicked on the Preferences button and checked on everything that was unchecked, like PCM, Capture Mux etc.  As I did so, more slider controls showed up in the Control dialog.

Everything else was on 0%, so I moved the PCM and Capture Mux to 100%, and set the Master to about 30%.  At that point, all sound was working for me.  Maybe it'll help you too.

---

### Post by antandrades on 2009-02-02
thanks guys.

i'll get to work and let you know how i get on.

cheers,
antb

---

### Post by antandrades on 2009-02-02
hi guys,

i am very happy to report the following additions to the menu.lst did the trick.

i added this line in # kopt line after ro (leaving a space).

noapic nolapic pci=noacpi acpi=off quiet splash

then i ran update-grub and rebooted.

on coming up the sound was totally fixed.

thanks for all your help!

ant:popcorn:

---

