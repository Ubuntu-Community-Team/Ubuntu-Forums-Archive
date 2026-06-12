---
title: "No headphone jack output on HP nx6110 in Ubuntu 9.10"
date: 2009-11-16
forum: Hardware
---

### Post by Steve Jorgensen on 2009-11-16
I was previously using Ubuntu 9.04 on my HP Compaq nx6110 and the headphone jack switch was working.  I did a from-scratch install of Ubuntu 9.10, and now I can only get sound out of the internal speakers.

I remember that initially, the jack switch didn't work in 9.04 either, and I fixed it by simply checking a box in the volume control to activate the switch.  I can't find any option like that now in gnome-volume-control though.

Any ideas?

Note:
I was previously using xfce and I'm now using Gnome.  I don't know if the mixer/volume control app is the same between the two.

---

### Post by Steve Jorgensen on 2009-11-16
By the way, I think this is the line in the lspci output that identifies my audio interface...

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

---

### Post by Steve Jorgensen on 2009-11-20
Any ideas how I might be able to get audio to work through the headphone jack?  I'm missing being able to listen to audio on decent speakers.  I don't care much whether the switch sensor works, just that I can somehow get the sound going through the jack.

---

### Post by Steve Jorgensen on 2009-11-20
Now that I had the symptoms right, I found the solution at [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/90609](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/90609).  gnome-volume-control does not have the capability to let me enable the jack switch.  I had to install gnome-alsamixer, which provides a check box to enable the jack switch.

---

### Post by nunojpg on 2009-12-16
Great. Solved mine also.

---

