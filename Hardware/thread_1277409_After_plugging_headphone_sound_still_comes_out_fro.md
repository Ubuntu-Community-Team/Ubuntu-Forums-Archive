---
title: "After plugging headphone sound still comes out from speakers on dell Vostro 1014"
date: 2009-09-28
forum: Hardware
---

### Post by su4232 on 2009-09-28
I just installed Ubuntu 9.04 on Dell Vostro 1014
i am having trouble with sound
laptop speakers still make sound after plugging in the headphone.
any help will be appreciated.
am gone through various posts made earlier but no success.
plz help
thanks in advance

"aplay -l" output-
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

"head -n 1 /proc/asound/card0/codec*"
Codec: Conexant ID 5067

---

### Post by Sultan-mrm on 2009-09-28
I had same problem on my acer but i have 3 ports sound input/output , pink for mic and green for sound out and black ( i don't know for what ) 

when i plug in my headphone in the green the sound is out from both (laptop speakers and headphone ) but when i plug it in the black one the sound is out from headphone only >>> maybe the story wil help you  :)

---

