---
title: "nvidia graphics card, Dell Latitude D820, and kernel 2.6.22-15"
date: 2008-07-16
forum: Hardware
---

### Post by RyanGT on 2008-07-16
I thought I already posted this, but haven't heard any responses and now can't find my own thread.  So, sorry if this is a double post.

I can't make my nvidia graphics card work with kernel 2.6.22-15.  It works just fine if I boot into the 2.6.22-14 kernel.  I have nvidia-glx-new installed.

Any ideas why one kernel would be fine and the other (2.6.22-15) repeatedly sends me to low resolution graphics mode?

Thanks,

Ryan

---

### Post by tylerious on 2008-07-29
I have the same problem! Any ideas, anybody?

---

### Post by evets25 on 2008-07-29
It can depend on how you installed the nvidia drivers. If you used the ubuntu restricted drivers manager, then everything should Just Work(tm). If, however, you downloaded the drivers from the nvidia webpage an installed them manually, then it would break everytime you do a kernel update. The nvidia driver and the kernel need to be upgraded together, that is, the version number on the nvidia driver package and the kernel version should match, or else you get this.

---

### Post by jimv on 2008-07-29
I use Envy to install Nvidia drivers.  It seems to keep them working through kernel upgrades better than most other methods.

Here's the the homepage for Envy with download and usage instructions:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by RyanGT on 2008-07-30
I am pretty sure I am just using the restricted drivers package.  Is there a way to make sure that is the case or to unistall a manual driver install if I have screwed it up?

---

### Post by evets25 on 2008-07-30
If you use envy, it can completely purge your system of drivers and make sure your system is clean before installing the nvidia drivers. I remember reading about this on a thread around here somewhere I just don't remember where, so look around.

---

### Post by RyanGT on 2008-07-30
Thanks.  I will try Envy shortly.  I think there is a blurb in the Envy FAQ about purging old drivers.

---

### Post by RyanGT on 2008-07-30
Envy seems to have solved my problem.  I did have to boot into the 2.6.22-15 kernel in low resolution graphics mode and run it from there, but it worked.

---

