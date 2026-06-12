---
title: "No nVidia Driver Available"
date: 2009-11-02
forum: Hardware
---

### Post by Maximus559 on 2009-11-02
I just got Ubuntu 9.10 installed after using it from the live CD several times. Installation went without a hitch, but now that it's running, there seems to be a problem with my nVidia MX 420 graphics card. The card works fine, but Ubuntu isn't giving me the option to install the necessary proprietary driver. Which is odd, because it did give me that option while I was running the OS off the LiveCD. I've checked this forum and Google, and it seems like everybody who has a similar problem already has the driver installed, but it's not showing up. That is **not** the problem I am having. The driver is not installed, and I am unable to install it. Anybody have any idea what the problem is?

---

### Post by oldsoundguy on 2009-11-02
you may need to add the restricted drivers.  (among some other things)
[http://guvnr.com/pc/karmic-repositories/](http://guvnr.com/pc/karmic-repositories/)

list of the repositories that you should have in your list besides the default ones.

Or you could try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
That one works for me!  (The NG version and follow the instructions.)

---

### Post by hansdown on 2009-11-02
Hi Maximus559.

If you click system> administration> hardware drivers, does it show up?

---

### Post by needTOS on 2009-11-02
I had the same problem with the 64-bit, and found out that if you can, have the ethernet plugged in while installing. When you boot into the install open the hardware drivers under the system> Administration> Hardware Drivers  , then it should load them for installation. Select the ones you want and choose activate.

-Steve

---

### Post by Maximus559 on 2009-11-02
Actually, hansdown, I just did that, and lo and behold, it shows up now. I did exactly the same thing earlier and it was blank. Thanks for all the replies; looks like this was a false alarm, though.

---

### Post by hansdown on 2009-11-03
Glad you fixed it Maximus559.

needTOS makes a really good point about having a connection while installing.

The last few clean installs that I've done have one thing in common.

At 82% install, it reads, "scanning mirror".When I look at my alpha-shield, it indicates that there is indeed data being downloaded.

---

