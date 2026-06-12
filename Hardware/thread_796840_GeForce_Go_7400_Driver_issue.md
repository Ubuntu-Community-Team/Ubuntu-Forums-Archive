---
title: "GeForce Go 7400 Driver issue"
date: 2008-05-16
forum: Hardware
---

### Post by Mutant Corn on 2008-05-16
So I've installed Ubuntu Studio(Hardy) for the 4th time. I know, without a doubt, that if I enable the driver for my video card, the system will fail to boot. (It gets past the screen where the bar goes back and forth, then just goes black.) The 3rd install was done simply to test this theory.

So far, this time, I have run update manager and changed the background...that's all. I dual boot with windows but I can't find a way to access the windows partition to get the driver...I think ubuntu being installed on a logical partition has something to do with it.

So...what do I do now? :confused:

edit: I have a Dell driver disk for windows, if that helps

---

### Post by overdrank on 2008-05-16
> **Mutant Corn said:**
> So I've installed Ubuntu Studio(Hardy) for the 4th time. I know, without a doubt, that if I enable the driver for my video card, the system will fail to boot. (It gets past the screen where the bar goes back and forth, then just goes black.) The 3rd install was done simply to test this theory.

So far, this time, I have run update manager and changed the background...that's all. I dual boot with windows but I can't find a way to access the windows partition to get the driver...I think ubuntu being installed on a logical partition has something to do with it.

So...what do I do now? :confused:

edit: I have a Dell driver disk for windows, if that helps
HI and you can look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
I have not used ubuntu studio but when I install the restricted drivers or envy, I have had to reconfigure my xorg and this solved my issues. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

