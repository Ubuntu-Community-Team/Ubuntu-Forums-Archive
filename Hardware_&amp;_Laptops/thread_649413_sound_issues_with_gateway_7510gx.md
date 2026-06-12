---
title: "sound issues with gateway 7510gx"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by adramalech on 2007-12-24
okay i have had my sound working for awhile then like last week after i have been with linux for a month it decides to not play any sound anymore...i can watch videos and play video games but with no sound!!!!:(  

i have looked at most threads dealing with the ac97 ati integrated sound card but i cant make heads our tails to why after so much research and troubleshooting it still wont work...i have eveyrthing unmuted in the volume control and have the sound up all the way to half way on each option...

now from my aplay -l command i get:

adramalech@adramalech:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
adramalech@adramalech:~$ 


and i have on the system -> Preferences -> Sound are all on autodetect...

now is there anyway that i could get my sound working again....:confused:

---

### Post by adramalech on 2007-12-26
okay further info if this should be able to help more....when i did lspci -v this is what i get for sound...

Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
        Subsystem: Gateway 2000 Unknown device 0506
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at c0503400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0

---

### Post by adramalech on 2007-12-26
okay i have finally found a comprehensive guide on fixing sound issues...i will try to get my sound working through this guide....

[http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is](http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is)

---

### Post by adramalech on 2007-12-26
okay it was something simple as my switches where all screwed up and had to spend a minute trying to get them straightened out...:lolflag:

besides stupid issues of switches and muted stuff that has been overlooked the guide above in the previous post really did help me with my other pc my tower that took forever to get sound working...:)

---

### Post by parian on 2008-01-25
Can you tell me what switches you made. I am a new Linux guy who recently installed Ubuntu on my 7510gx. I did something and lost sound. I have the same error messages you had. Thanks.

---

### Post by adramalech on 2008-05-13
okay when u right click onto the volume icon by the date, you open up volume control and check all the setting to make sure what you want isn't muted first off, then you will then check the switches tab and playback tabs to make sure the settings are correctly set to your needs.  if you cannot figure out how to see the switches tab, then you need to make sure that you have selected to show settings on certain items, like i have all the setting showing so i can make sure i have all options available to change around if the occasion occurs...

to do this you go to edit -> preferences then select what ever ones you want or need, then you will notice when you hit okay that there will be additional tabs showing...

---

