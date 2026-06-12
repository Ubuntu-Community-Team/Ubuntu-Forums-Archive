---
title: "Nvidia driver installation: glx-config not found"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by soupface on 2005-07-27
I've recently installed Hoary on an old Dell laptop with an nVidia GeForce2 chip. I tried to install the nVidia drivers (following [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver) and almost all of the threads here on ubuntuforums.org), but they don't seem to work.

The nVidia desktop settings program is there, and apt-get says that the nvidia-glx and nvidia-settings packages are installed, but when I try and run nvidia-glx-config enable, the console spits back "command not found."

I've tried altering the xorg.conf file so that the driver is "nvidia" (not "nv"), but when I do, X won't run.

Have I done something wrong? What can I do?

---

### Post by strikeforce on 2005-07-27
What where your exact commands when you installed the nvidia drivers.

---

### Post by soupface on 2005-07-27
I follow the steps from [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver) exactly:> sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable
The terminal responds, "nvidia-glx-config: command not found."

---

### Post by daigorobr on 2005-07-27
[QUOTE=soupface]I follow the steps from [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver) exactly:
The terminal responds, "nvidia-glx-config: command not found."[/QUOTE]
 From what I remember, it worked until a month ago, so I guess some upgrade wiped nvidia-glx-config out of the repos.

---

### Post by strikeforce on 2005-07-27
There is a kernel driver which needs to be installed as well.  I can't remember they exact file but I think its nvidia-kernel-module-`uname -r`

If that doesn't work you can compiled it from the Nvidia website.  Although you will need to install the kernel source.  I'll reply later on with all the details I did to get it working.  I'm at work at the moment.


*edit

[http://www.ubuntuforums.org/showthread.php?t=52209](http://www.ubuntuforums.org/showthread.php?t=52209)

Have a look at that post it should solve your issues and answer your questions.

---

### Post by soupface on 2005-07-27
[QUOTE=strikeforce]There is a kernel driver which needs to be installed as well.  I can't remember they exact file but I think its nvidia-kernel-module-`uname -r`[/QUOTE] Yeah, there is a package called nvidia-kernel-common which was installed when Ubuntu was first, uh, installed. I've got it.

> [http://www.ubuntuforums.org/showthread.php?t=52209](http://www.ubuntuforums.org/showthread.php?t=52209)

Have a look at that post it should solve your issues and answer your questions.
Not quite: [badboys107's solution](http://www.ubuntuforums.org/showpost.php?p=274422&postcount=12) doesn't help me. I still get the X-error blue-screen when I change the PCI and driver settings (just as I did when I changed only the driver setting) and the thread doesn't mention problems running nvidia-glx-config. What am I missing?

---

