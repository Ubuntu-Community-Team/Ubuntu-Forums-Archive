---
title: "Netbook Fujitsu M2010"
date: 2010-05-01
forum: Hardware
---

### Post by Cub3 on 2010-05-01
Hi,

I'm very new at Ubuntu and if got an question about a problem with my M2010 and 10.04.

Problem: The internal microphone doesn't work.

This bug was already known in UNR 9.10 and there were this great Compatibility Page were I found the solution for 9.10 

"All working out of the box: wifi, webcam, hotkeys, sound, usb, card  reader, touchpad, mic (jack works but not the build in, for Skype must  be enabled, default mute). etc. To make internal mic working it needs to  modify /etc/modprobe.d/alsa-base.conf and to add 'model=fujitsu' for  snd-hda-intel module. So last string of original alsa-base.conf becomes  as the following (without quotes) "options snd-hda-intel model=fujitsu  power_save=10 power_save_controller=N". Even when I connect my headset  for skype it mutes the netbooks own speakers. Compiz not tested (I dont  use), bluetooth not tested yet."

So i  guess in the new Ubuntu 10.04 you also have to edit  this alsa-base.conf but i have absolutely no idea what line I have to add or edit...

So I hope someone can help me!!

---

### Post by Cub3 on 2010-05-04
Has no one an idea what i have to edit in this alsa-base.conf??? ;(

---

