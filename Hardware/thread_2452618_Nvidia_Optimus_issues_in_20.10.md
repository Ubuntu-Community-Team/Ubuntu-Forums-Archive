---
title: "Nvidia Optimus issues in 20.10"
date: 2020-10-25
forum: Hardware
---

### Post by electragician on 2020-10-25
I have noticed across two separate installs that my 2 year old Dell G7 system with nVidia optimus graphics doesn't seem to be working correctly on 20.10. It works flawlessly on 20.04.

Once I use the nvidia settings GUI to swap to Intel graphics, I can no longer access the nVidia settings to change back to the nVidia graphics driver. The GUI launches, but just to a blank grey window, with no controls. I can swap back via the CLI, but the more pressing issue is that the nVidia chip doesn't seem to be shutting down in "Intel Mode" like it should. The laptop is generating a considerable amount of heat, and the area of the chassis that typically heats up when that chip is active is still hot.

Has anyone else seen anything like this in 20.10 on nVidia Optimus / hybrid graphics?

---

### Post by Yellow Pasque on 2020-10-26
Try using the new ondemand mode: [https://ubuntuforums.org/showthread.php?t=2450147&p=13985186#post13985186](https://ubuntuforums.org/showthread.php?t=2450147&p=13985186#post13985186)
(You probably don't need the PPA if nvidia is >=450 in Ubuntu 20.10)

---

