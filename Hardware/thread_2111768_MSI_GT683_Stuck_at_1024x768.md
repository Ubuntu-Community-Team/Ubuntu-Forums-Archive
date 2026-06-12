---
title: "MSI GT683 Stuck at 1024x768"
date: 2013-02-02
forum: Hardware
---

### Post by DeadlyEvolution on 2013-02-02
I installed Ubuntu, all the drivers that I needed for everything including my GPU and everything was working fine. I did my first Software Update in Ubuntu and then restarted. All was fine at that point. Then I shutdown my laptop, and unplugged it. When I restarted it without the laptop plugged in my resolution is now capped at 1024x768 even if I plug it back in. I believe this has something to do with my laptops hybrid graphics. I've searched the ins and outs of this forum and google trying to find a fix and none have deemed to be successful. My GPU is a NVidia GeForce GTX 570M. The default screen resolution is 1920x1080 which I cannot reach anymore. Also I cannot see the GUI 'Unity, I believe it's called' whatsoever. I just have the wallpaper on my screen and nothing else. I can pull up a terminal with CTRL + ALT + T still.


EDIT: After following [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely) I am successfully back at 1920x1080. Should I reinstall the NVidia Driver?
EDIT 2: I reinstalled the NVidia Driver - I get the same issue with the resolution. If I uninstall the driver, the issue is fixed. But then I don't get to use my GPU at all :X

---

### Post by Yellow Pasque on 2013-02-02
I just want to make sure this isn't an Optimus GPU setup. Post output of
```
lspci | grep VGA
```

---

### Post by DeadlyEvolution on 2013-02-02
> **Temüjin said:**
> I just want to make sure this isn't an Optimus GPU setup. Post output of
```
lspci | grep VGA
```
With or without the NVidia Driver installed?

Without the Driver installed it says

01:00.0 VGA compatible controller: NVIDIA Corporation Device 1210 (rev a1)


After doing a quick research on Optimus GPU I do believe that my laptop is indeed an optimus setup.

---

### Post by Yellow Pasque on 2013-02-02
> With or without the NVidia Driver installed?
Doesn't matter.
> After doing a quick research on Optimus GPU I do believe that my laptop is indeed an optimus setup.
No. If it was an Optimus setup, then an Intel GPU would show up on lspci too.

---

### Post by DeadlyEvolution on 2013-02-02
> **Temüjin said:**
> Doesn't matter.

No. If it was an Optimus setup, then an Intel GPU would show up on lspci too.

So any idea why it's doing this? Right now it's running OK without the VGA driver installed but kind of sucks to not have it installed.

---

