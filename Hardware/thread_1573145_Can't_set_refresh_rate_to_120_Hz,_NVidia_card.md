---
title: "Can't set refresh rate to 120 Hz, NVidia card"
date: 2010-09-12
forum: Hardware
---

### Post by oskarkv on 2010-09-12
Hey

I have a Samsung 2233RZ monitor that is capable to displaying 120 frames per second. But I haven't managed to set the refresh rate to 120 Hz. I have a NVidia GeForce 8800 GTS graphics card. I'm not using the latest drivers (that I got from software center) because they didn't work correctly; I got a lot of strange artifacts and bugs, dark lines that shouldn't have been there, etc. So I'm using an earlier version, version 173.

If I do sudo nividia-settings and select 120 Hz, apply and save, it says 120 Hz in there, in the X Server Settings program. But my monitor says 60 Hz, nvidia-settings -q RefreshRate says 60 Hz, and when I'm playing Quake I can feel that it is 60 Hz.

What can I do to actually get 120 Hz?

---

### Post by cascade9 on 2010-09-12
Refresh rate isnt really connected to frame rate like that (you can get more frames pre second than the refresh rate). 

I have no idea what is going on with your nvidia drivers. It could be something to do with the monitor and dual link DVI...you need dual link DVI to get refresh rates over 60Hz on a 1920x1080 or 1920x1200 monitor.

---

### Post by oskarkv on 2010-09-12
I was able to use 120 Hz in Windows. And the resolution is 1680x1050.

---

### Post by cascade9 on 2010-09-12
Even at 1680x1050 you need dual link DVI to get 120Hz. 

I dont know anything much about setting up dual link DVI though, so I'm not much help for you, sorry.

---

### Post by smeggs on 2010-12-21
I know this is an old post, but I was going through this issue as well. You need to enter nvidia-settings, and under your monitor's information section disable "Force Full GPU Scaling." Set your monitor to 120hz, then click apply and save to X Configuration File. 

milo@klendathu:~$nvidia-settings -q RefreshRate

  Attribute 'RefreshRate' (klendathu:0.0; display device: DFP-0): 60.00 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.
  Attribute 'RefreshRate' (klendathu:0.0; display device: DFP-1): 120.00 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

Mine wasn't updating because I had on full-gpu scaling, every time you close nvidia-settings it will revert. Also, make sure you save to x config when you do this, it won't save that setting unless you do. Worked for me, let me know if you're still having this problem/if this fixes it.

---

### Post by newdev on 2011-01-16
> **smeggs said:**
> You need to enter nvidia-settings, and under your monitor's information section disable "Force Full GPU Scaling." Set your monitor to 120hz, then click apply and save to X Configuration File. 

It worked for me! =D> Thank you very much!

---

### Post by themoddingden on 2011-08-21
Hi;
I got it to give me the option  but it will not stay as default resolution .
It defaults to 1024x768 which sucks.
I have to keep setting it  after boot up.
I'll post my xorg tomorrow .

---

