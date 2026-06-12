---
title: "No sound after minimal install"
date: 2008-12-01
forum: Hardware
---

### Post by junglebear on 2008-12-01
Here's the problem.

I've done a minimal install of Ubuntu with XFCE, but I have no sound. 

My card is recognised in lspci and I've got alsa-base, alsa-oss and alsa-utils installed, all channels unmuted etc. but still no sound.

I've had various distro's (including Ubuntu) installed on the same machine before and never had this problem. Anyone have any ideas?

Thanks
jb

---

### Post by sgeoxd on 2008-12-01
I am having the same issue, using an Intel CH5 on board audio from an Asus P4P800 SE.  aplay -l and aplay -L show no sound card unless I startx with sudo.  Then sound works normally.  May try that to see if you can get something. Currently working on finding a way around starting everything with sudo to get sound - already added my user to the sound group with no luck.

---

### Post by ralph.p on 2008-12-01
I also have [no sound](http://ubuntuforums.org/showthread.php?t=996694)

> unless I startx with sudo
can you explain that please?

---

### Post by sgeoxd on 2009-04-10
Sorry for the delay, hopefully you haven't given up.  I did find a work around, quite simple really.  On later versions of Ubuntu, especially when compiling Alsa, it is necessary to add yourself to the right group.  Just be sure to replace "username" with whatever you login as:  
```
sudo usermod -a -G audio username
```

This has caused problems when compiling my own NVIDIA drivers.  Symptom is just a flashing screen when you try to startX.  Same fix, different group:
```
sudo usermod -a -G video username
```

---

