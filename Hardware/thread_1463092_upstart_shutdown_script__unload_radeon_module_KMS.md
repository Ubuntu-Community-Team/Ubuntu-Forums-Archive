---
title: "upstart shutdown script / unload radeon module KMS"
date: 2010-04-26
forum: Hardware
---

### Post by cak3 on 2010-04-26
I have an HP tx2500z laptop running Xubuntu 10.04. It has a Radeon HD3200 (RS780) GPU. I am using the free driver (see attached xorg.conf) and it works great, except the computer does not poweroff on halt. Turns out, this is because it is unable to unload the Radeon module when KMS (kernel modesetting) is enabled. I can verify this by adding "radeon.modeset=0" to my grub command line, which disabled KMS, and then it shuts down properly. I submitted this launchpad bug about it [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/569271](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/569271)

Well, I have come up with a sort of workaround. I created an init script, which I called "uloadradeon" (attached), put it in /etc/init.d, and ran "update-rc.d uloadradeon stop 80 0 ." to create symlinks in /etc/rc0.d so that it will run at shutdown. 

So far so good. I tested in first in recovery (single-user) mode, just calling "shutdown -h now" and it shutdown perfectly (it wasn't able to do so before I added that script). 

Unfortunately, that wasn't the end. It still was unable to shutdown when I was in normal mode. I am still not entirely sure what is causing this, but I suspect it is related to upstart, although I think upstart should still run the old sysv init scripts when changing runlevels, I am not sure, and I haven't been able to find any good documentation on upstart, particularly how to get a script to run at a certain point during shutdown. 

Anyone know anything about this?

---

### Post by cak3 on 2010-04-26
I figured out how to do it. I created an upstart job to do it, and placed it in /etc/init

the job file is attached, if anyone is interested.

---

### Post by BrokeMahPC on 2010-05-01
Hi - got your PM.
I don't have the same problem - I was trying out kernel 2.6.34 and possibly didn't install it correctly. Fresh installed 2.6.32-21 and it's fine now.
The shutdown fault somehow burned my Asus Expressgate software which is stored in solid state memory on the motherboard and I have yet to see if it will reinstall!

---

### Post by nmehta6 on 2010-05-15
Cak3,

I have a an hp tx2000 tablet and I am not able to shut down the computer either. I downloaded unloadradeon.conf file. I am not able to paste it in the /etc/init directory.

I am very new to linux. Could you please help me out?

Thanks

---

### Post by nmehta6 on 2010-05-15
I got it.

Thanks for the script. It works for tx2000 tablet as well.

---

### Post by Docaltmed on 2010-06-06
I must be doing something wrong. I downloaded the file, put it in the correct directory, and the first time the shutdown worked. Ever since then, it has hung on shutdown again.

Any suggestions?

---

### Post by Docaltmed on 2010-06-07
Interesting. Each time I replace the file in etc/init/ the unloader will work exactly once and shutdown is flawless. When I reboot, it runs fsck and then shutdown hangs again as it did previously.

---

### Post by Aphotic on 2010-07-16
The problem I encounter is that composition and 3d aren't supported by the free radeon driver. (At least that's what the wiki says and I am observing with my system. "2D Modesetting")

I run a hp tx2500 with the ati hd3200.

Are there any solutions similar to yours in regards to the fglrx driver? (I like my eyecandy damn it!)

---

