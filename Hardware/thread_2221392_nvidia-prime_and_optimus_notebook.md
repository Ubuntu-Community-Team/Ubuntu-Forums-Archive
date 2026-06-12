---
title: "nvidia-prime and optimus notebook"
date: 2014-05-01
forum: Hardware
---

### Post by renato3 on 2014-05-01
Hi, I'm using Ubuntu 14.04 on a Dell Inspiron 14R 5421. I have two cards, integrated Intel and dedicated Nvidia GT 730M. I installed the proprietay nvidia 331.38 by going on Settings --> Softwares & update --> Additional Drivers. Here is a print screen:

[IMG]http://s27.postimg.org/xegm9zqc3/Screenshot_from_2014_05_02_00_21_50.png[/IMG]

Then I installed prime-indicator to be able to rapid switch between intel and nvidia cards. My Nvidia X Server settings was like this image (this is not a printscreen of mine, but it was very similar to this):

[IMG]http://dl.dropboxusercontent.com/u/1113424/img/nvidia-prime-profiles.jpg[/IMG]

glxgears was showing high FPS. **EVERYTHING WAS PERFECT!** But then I installed a LOT of packages, I removed the package **linux-image-generic** (because apt-get was complaining it was safe to remove) and now my nvidia card is not working anymore and I don't know exactly why :(

prime-indicator icon is gone and my Nvidia X Server settings now look like this:

[IMG]http://s9.postimg.org/5m2ilzwdr/Screenshot_from_2014_05_02_00_19_28.png[/IMG]

How can I revert things back as they were, without making a clean install? I guess I have to purge some packages and reinstall them, right? Which packages should I purge and reinstall?

---

### Post by renato3 on 2014-05-02
```
$ sudo apt-get purge nvidia-331 nvidia-opencl-icd-331 nvidia-settings nvidia-libopencl1-331 nvidia-prime prime-indicator
$ sudo apt-get install nvidia-331 nvidia-opencl-icd-331 nvidia-settings nvidia-libopencl1-331 nvidia-prime prime-indicator
```

Everything is back to normal now!

---

