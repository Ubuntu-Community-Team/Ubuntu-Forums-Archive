---
title: "help installing nVidia 6200"
date: 2008-06-10
forum: Hardware
---

### Post by melat0nin on 2008-06-10
Hi all

I've just put a new 6200 into my aging machine to replace a dying 9800 Pro.

I booted up, got the bullet-proof X screen asking for further configuration.  I selected my monitor and correct resolution, but when I get into Ubuntu I'm limited to 800x600 and the monitor is 'unknown'.

I got the prompt saying a restricted driver is available, so I installed that and rebooted, but the same thing happened.  The prompt then appeared again(!) and I re-installed it, but I'm still at this low resolution without 3D acceleration.  The Restricted Drivers Manager says that the 'NVIDIA accelerated graphics driver (latest cards)' is in use (green light), even though the checkbox next to it is not checked.

Any help to get this working would be much appreciated! :)

---

### Post by duckwaltz on 2008-06-10
Have you tried using nvidia's proprietary settings program. If the restricted driver is indeed installed, then the program should be under System -> Administration -> NVIDIA X Server Settings. This tool has a ton of options. Also, are you using the nvidia-glx or the nvidia-glx-new driver?

---

### Post by melat0nin on 2008-06-10
> **duckwaltz said:**
> Have you tried using nvidia's proprietary settings program. If the restricted driver is indeed installed, then the program should be under System -> Administration -> NVIDIA X Server Settings. This tool has a ton of options. Also, are you using the nvidia-glx or the nvidia-glx-new driver?


I just came back into Hardy from XP, and had the same problem with "bulletproof X" coming up.. the default driver was vesa, so I accepted that.

At the moment therefore I'm sure I@m not using the nvidia driver (apart from the dodgy resolution, there is no nvidia settings program).

My inkling is that the Restricted Drivers Manager is not properly installing the nvidia driver.  I don't want to attempt it myself without proper instructions, in case I make things worse.

Any thoughts?

---

### Post by melat0nin on 2008-06-10
Well I've got somewhere, kind of. 

I saw a recent post recommending Envy, so I ran that and installed the nvidia driver.  Now I have NVIDIA X Server Settings in my System > Administration menu, but I get an error when I run it.  I followed the instruction (running nvidia-xconfig and restarting X) but that hasn't helped.

I'm still stuck at 800x600 and I don't have 3D acceleration (glxgears won't run.. quits with error saying GLX extension is missing).

In the Hardware Drivers applet though, it says the NVIDIA driver is enabled and in use.

---

### Post by melat0nin on 2008-06-10
I tried installing using the steps on this post: [http://ubuntuforums.org/showpost.php?p=5118982&postcount=2](http://ubuntuforums.org/showpost.php?p=5118982&postcount=2)

But when I try to run the Nvidia driver, I get messages about my kernel's source being absent, so the installation can't complete.

Any thoughts? Help much appreciated :)

---

### Post by duckwaltz on 2008-06-10
I believe this has moved beyond my realm of experience. The only thing I can suggest is that you attempt to add your kernel's source to your computer. So you just install whatever-kernel-source package I do believe and then try again?

---

### Post by melat0nin on 2008-06-10
To avoid a lot of headaches, I've just re-installed Hardy from scratch.

I'm now sitting with a clean installation, fully updated, running at the correct resolution (1440x900) using the default Hardy driver.

So, next step:  what's the best method to get the nvidia driver installed?  Just the Hardware Drivers applet?

I don't want to get myself into the same endless loop of failures, so I'd rather do it right the first time and be done with it! ;)

---

### Post by stchman on 2008-06-10
> **melat0nin said:**
> Hi all

I've just put a new 6200 into my aging machine to replace a dying 9800 Pro.

I booted up, got the bullet-proof X screen asking for further configuration.  I selected my monitor and correct resolution, but when I get into Ubuntu I'm limited to 800x600 and the monitor is 'unknown'.

I got the prompt saying a restricted driver is available, so I installed that and rebooted, but the same thing happened.  The prompt then appeared again(!) and I re-installed it, but I'm still at this low resolution without 3D acceleration.  The Restricted Drivers Manager says that the 'NVIDIA accelerated graphics driver (latest cards)' is in use (green light), even though the checkbox next to it is not checked.

Any help to get this working would be much appreciated! :)

Try this in a terminal:

```
sudo apt-get update
sudo apt-get install nvidia-glx-new

```

If the restricted driver is indeed installed then not much should happen.

If it does install a reboot will be necessary.

After that type:

```
sudo apt-get install nvidia-settings
nvidia-settings
```

This will bring up the nvidia settings GUI.  You can select the resolution from this menu.  If the settings don't stick then do:

```
sudo nvidia-settings
```

---

### Post by stchman on 2008-06-10
> **melat0nin said:**
> To avoid a lot of headaches, I've just re-installed Hardy from scratch.

I'm now sitting with a clean installation, fully updated, running at the correct resolution (1440x900) using the default Hardy driver.

So, next step:  what's the best method to get the nvidia driver installed?  Just the Hardware Drivers applet?

I don't want to get myself into the same endless loop of failures, so I'd rather do it right the first time and be done with it! ;)

If this is the case then install the Restricted Driver and you are in business.

---

### Post by melat0nin on 2008-06-10
> **stchman said:**
> If this is the case then install the Restricted Driver and you are in business.

That has worked great, thanks :)

---

### Post by ntripcevich on 2008-09-15
Hi---
I'm having the same problem described here where the video appears in Hardware Drivers but if I try to Enable it I get a configuration window and low res monitor upon reboot.
I've followed the directions here but I can't seem to initiate the driver from the Administration > NVIDIA X Server Settings menu.

I get an alert reading
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
Running that command with sudo I get the following msg "Using X configuration file: "/etc/X11/xorg.conf"."
If I Log out and Log in to restart the X Server I'm back to the "video unavailable" error it asks me to configure the video.

I have two drivers available, one called "nv" and another called "nvidia" but neither are useable by the system (Hearty Heron, 8.04). The only video setting to do better than 800x600 resolution is the built in video driver.

I've also tried the EnvyNG method for getting a working nvidia 6200 driver but with no luck. Are these different drivers clashing (need to uninstall those not in use)?
Thanks for any leads on this.

---

