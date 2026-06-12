---
title: "After updgrading to Ubuntu 15.10 from 15.04 There is a problem with the bluetooth"
date: 2015-10-29
forum: Hardware
---

### Post by daniii10 on 2015-10-29
Yesterday I upgrade my system (Dell Inspiron 5720) from 15.04 to 15.10, and now I have a problem with the bluetooth headset.

I use Nokia BH-905i headset with microphone for calls and stereo the problem now there is no sound. The headset connected to the computer through bluetooth, but when I go to sound settings and try to choose the headset settings it stays in speaker settings and there is no sounds. I think somehow the bluetooth driver on the computer can't recognize the stereo (A2DP) on the headset. Before the upgrade everything was fine.
Any ideas how I can fix this?

[[IMG]http://s22.postimg.org/qwgk79kz5/bluetooth_headset.jpg[/IMG]]("http://postimage.org/")
[URL="http://postimage.org/"]photo hosting sites


[/URL]

---

### Post by daniii10 on 2015-11-05
I found the solution. I installed blueman from [here]("http://www.ubuntuupdates.org/package/core/wily/universe/base/blueman") and paired the headset from there.

---

### Post by ogilvierothchild on 2015-11-11
Thanks this worked for me as well, with multiple a2dp bluetooth headsets.

---

### Post by jkt-nocrack on 2015-11-23
Hi Danii10,

I have the exact same problem, but on a Dell 7000 serie.
Installing Blueman from your link didn't help on my case. I can still link the sound device with no problem, but can't seem to get the device in the sound output list... Did you do anything else than just installing blueman ?

Thanks

---

