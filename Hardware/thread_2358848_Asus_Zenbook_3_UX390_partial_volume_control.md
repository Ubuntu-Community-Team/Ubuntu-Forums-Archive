---
title: "Asus Zenbook 3 UX390 partial volume control"
date: 2017-04-18
forum: Hardware
---

### Post by natedaswas on 2017-04-18
There was a previous thread about this laptop that was trying to cover 5 different issues and didn't really resolve them completely. It was suggested that individual threads be made.

I recently installed ubuntu 16.04 on my new asus zenbook. There are very few problems but one of the more annoying ones is the volume control. Out of the box the media keys would control the internal audio volume graphics and supposedly adjust the volume but it would either be 0% or 100% Anything besides mute was 100% audio volume.

In browser controls work to change the volume but not the ubuntu volume controls.

After messing around in the below mentioned file, it seems I was able to get it so using ubuntu controls I now have 0%, 50% and 100% but those are only the first 3 pegs on the volume control. So graphically, once the slider is at 10% I have reached 100% volume.
/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common

Would love any direction in solving this issue.

---

