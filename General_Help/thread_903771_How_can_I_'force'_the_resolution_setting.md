---
title: "How can I 'force' the resolution setting?"
date: 2008-08-28
forum: General Help
---

### Post by bsmith1051 on 2008-08-28
I have a new 8.04.1 install on an ATI 740G motherboard.  In general everything works great, and I'm using the Ubuntu-supported proprietary driver for the on-board X1250 video-card.

The problem is that the video setting is only set properly if I have my monitor 'on' during start-up.  I'm using 2 computers on a KVM switch and if I continue using my other computer, then switch to the Ubuntu box, it'll be running at 640x480 and refuse to let me re-select the full 1280x1024.

Is there a way to edit xorg.conf so that it always uses 1280x1024 even if doesn't think the monitor supports it?

---

### Post by jonian_g on 2008-08-28
Open a terminal and type:

```
sudo displayconfig-gtk
```

On the window that comes up look if your monitor model is next to "Model:". If its not, click on it and find it in the list.
If its not in the list, instert in the drive the disc that came with your monitor, click "add" and locate the .inf file in the disc. If you don't have the disc choose a generic model with the maximum res your monitor can handle (probably 1280x1024).

I would recommend also to install the latest ati drivers with envy.

To install envy, open a terminal and type:

```
sudo apt-get install envyng-gtk
```

Then go to Applications>System>EnvyNG and install the drivers.

---

### Post by bsmith1051 on 2008-08-28
Thanks, I think that'll do it!  The default was "plug-n-play" which is exactly the problem when using my KVM.  Instead I set it to "LCD 1280x1024"

re ATI and Envy, I've been 'bitten' before by kernel upgrades breaking the vendor-supplied drivers.  Whereas the Ubuntu-supplied 'proprietary' drivers are guaranteed not to break, right?

---

### Post by jonian_g on 2008-08-29
This is not the case with envy. Drivers installed with envy don't break on kernel updates.

---

### Post by tuxxy on 2008-08-29
I have that card, are you editing/saving the resolution in the catalyst control center? also make sure you run this as sudo as it might not save it otherwise.

Even if you get it working there still going to be some problems with that card im afraid its the ATI drivers.

---

### Post by bsmith1051 on 2008-08-29
> **jonian_g said:**
> This is not the case with envy. Drivers installed with envy don't break on kernel updates.
That wasn't my experience last year with Ubuntu 7.10, Envy, and the then-current Nvidia driver.  Is there something different about how EnvyNG works?  Unfortunately, I don't understand the particulars about how/why the kernel upgrade broke my system so I don't know how to tell if it was something to do with Envy or not.

---

### Post by jonian_g on 2008-08-29
I have the nvidia drivers installed with envy since I first installed Hardy. Kernel has been updated 4 times and I had no problems.

---

### Post by bsmith1051 on 2008-09-03
> **jonian_g said:**
> I have the nvidia drivers installed with envy since I first installed Hardy. Kernel has been updated 4 times and I had no problems.
That's great to know, thanks!  Hopefully I'll have the same experience with the official ATI drivers.

P.S.  The 'displayconfig-gtk' setting didn't work, my LCD still reports "Unknown resolution - Unable to display" when I boot the system with the KVM set to the other computer.  So now I'm going to try EnvyNG and the latest ATI driver.

P.P.S.  Before I upgraded I had an old Nvidia MX400 running on the Ubuntu-supplied 'proprietary' drivers.  I had no problems with the KVM.

---

### Post by Zimmer on 2008-09-03
Have you read the xorg.log produced? I bet it reports a failure to read the EDID info from a monitor it cannot see.
Let me know..

> There are several causes for EDID fail reads. One is if you're using a truly ancient monitor from the days before EDID. A second is if you're using a video extension cable, KVM, or other piece of equipment connected between the monitor and the video card that lacks the EDID wire. In both these cases, you have a hardware issue, and there's nothing that can be done in software to get around it - you'll need to either get different hardware, or familiarize yourself with xorg.conf syntax and do your configuration yourself.
from 
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760)

---

### Post by bsmith1051 on 2008-09-03
> familiarize yourself with xorg.conf syntax and do your configuration yourself.
Any suggestions on how to do this?  I've already tried running 'displayconfig-gtk' and (supposedly) forcing it to use LCD 1280x1024 @ 60 Hz.  But the problem might actually be that the KVM switch reports EDID info which is incompatible with the monitor, and Hardy is trying to use it rather than the preset.

I'll report back tomorrow about the newer ATI driver...

---

### Post by Zimmer on 2008-09-04
> **bsmith1051 said:**
> Any suggestions on how to do this?  I've already tried running 'displayconfig-gtk' and (supposedly) forcing it to use LCD 1280x1024 @ 60 Hz.  But the problem might actually be that the KVM switch reports EDID info which is incompatible with the monitor, and Hardy is trying to use it rather than the preset.

I'll report back tomorrow about the newer ATI driver...


[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/index.html)
Yes, I know you have an ATI card, but the info on how to set up your xorg.conf by hand could be of use.(unless some options are not recognised by the ATI driver...)

I have now used the Option "UseEdid" "False" in the screen section of the xorg.conf with  a good result. 
This means I have had to construct the valid modeline statements for my my monitor and a few other tweaks, such as DPI.  

I am still working on this subject as I am not confident that everything is ok, since Gnome appears to report the screen settings made incorrectly (or calculated using xrandr, which reports things in another way I do not yet totally understand).
I loaded nvidia-settings and that reported the resolution corrrectly (or at least what I expected).... so which settings report is correct???

---

