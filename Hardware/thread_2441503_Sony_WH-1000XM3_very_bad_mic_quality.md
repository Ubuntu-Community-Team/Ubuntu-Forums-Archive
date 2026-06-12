---
title: "Sony WH-1000XM3 very bad mic quality"
date: 2020-04-24
forum: Hardware
---

### Post by di-mk1 on 2020-04-24
I've done extensive reading and several workarounds trying to figure  out why the mic of my new SONY 1000MX3 headset performs so poorly in Ubuntu 18.04 Budgie. My  voice sounds like I'm talking in a tube or something.
  What I've done so far:
  
[LIST=1]
[*]I installed bluez 5.50. 
[*]I installed blueman and I can connect to my headset in a2dp profile. Sound is amazing, but as a2dp is unidirectional I have no mic. 
[*]If I launch Sound Settings, I go to Input -> Select Bluetooth SONY 1000MX3. Then the mic of the headset becomes active and when I talk I see the bars moving, although I should speak very loud for the bars to go to the far end. At the same time the output reverts back to HSP/HFP and obviously sound is like a landline. 
[*]Still with HSP/HFP selected, I launch Microsoft Teams to do a test  call and record my voice. I can hear my voice but as said it sounds a  bit choppy and like I'm talking from a tube or something. A deep voice  with lots of bass.
[/LIST]
  I'm aware of the bug [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1838151"),  but was wondering if there is any other workaround to use better  quality settings for HFP/HSP. I can live with HSP/HFP during calls at  work and then revert back to a2dp for my music, but the mic quality is  unacceptable. I've also noticed that the headset does not appear in alsamixer.
  Any ideas?

---

### Post by mörgæs on 2020-04-24
Judged by the bug report it seems like Chromium OS has applied the patch. Have you tried if the sound is better here?

---

