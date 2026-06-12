---
title: "Toshiba T-235 and 10.04"
date: 2010-12-23
forum: Hardware
---

### Post by saldarji on 2010-12-23
I purchased a Toshiba T-235 and I am generally happy with the laptop.  I was able to get 10.04 running flawlessly, after a little bit of trial and error.  I hope that this post will save someone some trouble.

1.  I tried using 10.10, but there were ACPI issues.  The only way I could get the laptop to run was putting noacpi as a flag during startup.  I'm not sure if this is damaging or what, so I went with 10.04 instead.

2.  You can use the Ubuntu installer to resize your partition and dual-boot Windows and Ubuntu.  The windows install may go into "recovery mode" but it should recover and work as before.

3.  The installation is flawless - everything works as it should, with one exception - audio in.  There is an easy fix for this.  Just remember to make sure that the audio is turned up, and not muted, in Alsa config.

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
sudo reboot now
```

Hope this helps!

---

