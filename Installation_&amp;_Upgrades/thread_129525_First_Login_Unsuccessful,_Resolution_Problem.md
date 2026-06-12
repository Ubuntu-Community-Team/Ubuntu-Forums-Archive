---
title: "First Login Unsuccessful, Resolution Problem?"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by leemobile on 2006-02-13
Hi,

So I installed Ubuntu, reboot, and get to the login screen.

It's all nice and pretty.  I enter in my login and password, and hit login.

Then my screen presents a weird image, it looks like there might be something wrong with the resolution.  I can only see tiny white lines on a dark blue background scrunched up.

At this point I can't do anything.  Maybe it's a resolution problem?

Is there any way I can change resolution safely?  

Also, my system runs on an Athlon64 porcessor and I'm using the x86 installation disc.  Could this be a problem as well? 

Thanks,

Lee

---

### Post by encompass on 2006-02-13
Right off... I don't think haveing x86 install is bad at all, many people don't because they want more software, and x86 gives that.
Second about the resolution... see if you can see a console... when at that messed up screen, or before, try pressing ctrl-alt-f1 that should drop you to a console... login from there... and type  sudo dpkg-reconfigure xserver-xorg and make sure that you have seleted the correct driver for your graphics card.  It could be, from your explaination a bad selection of a driver.  If you are unsure about anything in the configure process just press enter to stay with the previous setting.  it could also be that you resolution is set to high. when selection the resolutions that you want to use... select the highest setting to be 1024x768 and see what happens.
If these steps don't help... feel free to enter you graphics card information, it wouldn't hurt if you included your monitor too.

---

### Post by heimo on 2006-02-13
Hit ctrl+alt+F1, log in and edit /etc/X11/xorg.conf OR run
```
sudo dpkg-reconfigure xserver-xorg
```

Additional information:
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by aysiu on 2006-02-13
Press Control-Alt-F1.
Log in.
Then type ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by leemobile on 2006-02-14
Hi, I tried to reconfigured the resolution.

I was able to get to the login screen in a lower resolution.

In the lower resolution, the splash screen when I login shows up EXCEPT it's all garbled.

I forgot to mention that my video card is a Nvidia Gefore 7800 GT PCI-E, I'm thinking maybe the default drivers for Ubuntu 5.10 doesn't support this?

Hmmm... any thoughts?

---

### Post by leemobile on 2006-02-15
Just as a conclusion, I got things working \\:D/ 

It appears that the NV drivers don't support the 7800 GT just yet, so I installed the Nvidia drivers and everything ran fine.

So all you 7800 GT PCI-E folks out there, be warned!  A workaround to get in is to use the vesa driver to get X working, but it doesn't quite support all the proper resolutions.

---

