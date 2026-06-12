---
title: "No sound from external (S/PDIF) speakers"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by ze_otter on 2007-08-13
I've searched many forums and looked through the similar threads on this board, but haven't been able to find an answer to my problem, which is that I can't get any sound out of my external speaker system.

I recently installed Kubuntu 7.04, and got it working otherwise, but the sound system is still a mess. The analog headphones work ok, but the speaker system that's connected to the integrated sound chip (recognized as VIA 8237/Realtek ALC850 in alsamixer) through my motherboards (Asus A8V) S/PDIF coaxial out remains silent. I've checked all the settings, and nothing is muted, checking/unchecking "external amp" has no effect. Any ideas?

After searching even more thoroughly, I found several threads that suggested playing around with the device settings, but I can't figure out what I should do. Here's the output from aplay -l 

card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

It doesn't seem to contain digital outputs, and when trying various settings such as aplay -D hw:0,0 or 0,1 and trying to play a .wav file, I still can't get any sound out of my speakers.

Final edit: now I somehow managed to get sound out of my speakers while losing it from the headphones. No idea how, though.

---

