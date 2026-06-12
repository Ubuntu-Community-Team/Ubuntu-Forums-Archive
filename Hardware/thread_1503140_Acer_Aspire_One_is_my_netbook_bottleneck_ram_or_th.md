---
title: "Acer Aspire One: is my netbook bottleneck ram or the video processor?"
date: 2010-06-06
forum: Hardware
---

### Post by thomsec on 2010-06-06
Howdy, I've got an Acer aspire d150 with 1gb ram. I need to run google earth for an upcoming trip, but it runs really sluggishly on the aspire, even with the colors and anisotropic filtering off. So...I'm considering either purchasing a 15.6" laptop or upgrading the ram on the aspire. But if the bottleneck is the video card the ram would be a waste of money. Anyone out there have any advice?

---

### Post by an0dos on 2010-06-06
Based on the recommended system requirements for Google Earth on Google's website, your netbook should have enough ram and a fast enough processor to run Google Earth smoothly (assuming you have a good internet connection). I seem to remember that there were some performance issues involving the drivers for Intel video cards, but this may be old information.

Why don't you run glxgears and post the output here.

---

### Post by thomsec on 2010-06-06
Thanks for the response. Internet bandwidth is definitely not the issue.
Here is the output from glxgears
309 frames in 5.0 seconds - maximized
483 frames in 5.0 seconds - maximized
1048 frames in 5.0 seconds - unmaximized
1058 frames in 5.0 seconds - unmaximized
1052 frames in 5.0 seconds - unmaximized
646 frames in 5.0 seconds - maximized
344 frames in 5.0 seconds - maximized
669 frames in 5.0 seconds - maximized

---

### Post by an0dos on 2010-06-06
Please post the contents of the "device" section of your xorg.conf. It is located at /etc/X11/xorg.conf.

If you have compiz (desktop effects) turned on, have you tried running Google Earth with them turned off?

---

### Post by thomsec on 2010-06-06
I do not have desktop effects turned on. In fact, the whole page is greyed out so I couldn't turn them on if I wanted to. No xorg.conf file with 10.04.
Thanks,
Charlie

---

### Post by an0dos on 2010-06-06
Check out the thread here: [http://wwww.ubuntuforums.org/showthread.php?t=1130582&highlight=intel+GMA950.]("http://wwww.ubuntuforums.org/showthread.php?t=1130582&highlight=intel+GMA950")

You can also check out the wiki page here: [https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

---

### Post by thomsec on 2010-06-06
Thanks, I checked out the link and found this: 
Re: HOWTO: Jaunty Intel Graphics Performance Guide
Quote:
Originally Posted by fktt View Post
This may be a stupid question, but would this quide be of use on 10.04 with a gma 950?

ps. I'm running the acer apire one(AOA150) zg5.
No, 10.04 has the latest kernel, DRM, and Intel drivers which fix the problems with 3D speeds. There is a more recent driver from intel which fixes a lot of speed issues but it may not be in the repos yet.

---

### Post by libssd on 2010-06-19
I can't offer any solutions, only report that Google Earth runs at an acceptable speed on my AA1 D150.

---

### Post by sandy8925 on 2010-06-20
It should run ok.Since the laptop has an intel graphics card,it should be working fine out of the box. check if you can enable compiz? if compiz is enabled maybe it's slowing down google earth. also if you're running gnome then add the cpu frequency widget and set the frequency to the highest one. this forces the cpu to run at full speed. check if google earth runs ok now?

---

