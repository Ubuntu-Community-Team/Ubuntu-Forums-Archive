---
title: "Tried to install 180.22 drivers, now all hell broke loose"
date: 2009-01-21
forum: Hardware
---

### Post by GCFreak on 2009-01-21
Hi,

I previously had the 177 drivers working on my Mythbuntu media centre, but I couldn't get XvMC to work so I thought it might be drivers, so I installed the 180.22 drivers from the NVIDIA website. But now, it boots into low graphics mode. It didn't work, and it doesn't let me see any logs. So I just installed the 180 drivers from Synaptic, getting same things. I tried to roll back to the 177 drivers, does the same thing too.

I've had rotten luck with Mythbuntu so far, and some of my threads don't get answered so yeah, please help. =)

---

### Post by GCFreak on 2009-01-21
Bump. Sorry if I seem impatient, but alot of my threads have been unanswered and I've had to fend for myself but here I have no idea what I'm doing, your help would be very appreciated.

---

### Post by dabl on 2009-01-21
Install EnvyNG with Synaptic.

Ctrl-Alt-Backspace out of the X server and shut it down with ```
/etc/init.d/gdm stop
```

Then run EnvyNG in text mode

```
sudo envyng -t
```

First, use the menu to _remove/uninstall_ the proprietary driver.  Then, when it is finished, _install_ the proprietary driver, and follow the prompts to write a new xorg.conf file and start the X server.

---

### Post by GCFreak on 2009-01-21
Hi dabl, and thanks for the quick reply! =)

I followed your instructions, but EnvyNG didn't have an option to rebuild xorg.conf, so I simply did it using nvidia-xconfig, I restarted the computer, and it's still in low graphics mode...do I need to rebuild xorg.conf with something else?

Thanks.

---

### Post by GCFreak on 2009-01-21
This might help, at the moment when it says it's running it's in low graphics mode, it says it couldn't detect the screen, video card and input settings properly and I have to configure it myself.

Thanks.

---

### Post by Big_Kahunaca on 2009-01-22
I had something similar happen on my laptop after installing the driver from the Nvidia web site.

I had to install the OLD driver (version 96) from the repo, reboot, then searched in Synaptic for "nvidia" and it was able to pull up the 180.11 drivers.

I installed the glx, modaliases, kernel-source, rebooted and it worked fine.

Give it a try if you're stuck!

---

### Post by dabl on 2009-01-22
You're saying it boots into "low graphics mode" -- I'm not sure I understand.  If nvidia-xconfig did it's job correctly, then possibly the issue is more with the monitor than the card itself.

With my 9600GT, and a big Samsung SyncMaster 1100, I need to use "vga=837" as the boot option to get it to both (a) show the logo/boot splash and (b) start KDM correctly, so I can use the GUI login.  I previously tried "xforcevesa", which showed the boot splash but half the time would crap out on the login GUI.  I could also use "vga=788", which would start KDM nicely, but the boot splash was split in a strange manner across the screen.

I would say try some experiments with boot options and see if can find one that makes it happy.

---

### Post by stdPikachu on 2009-01-22
Can you see if the nVidia module is loaded?

lsmod | grep nvidia

If it is loaded, can you see which version it is?

cat /proc/drivers/nvidia/version

I recently had to jump through a few hoops to get the 180.xx drivers installed on 8.04 but got it working in the end.

---

### Post by GCFreak on 2009-01-22
lsmod | grep nvidia:
```
nvidia               7082420  0 
agpgart                42184  1 nvidia
i2c_core               31892  9 mt2060,dvb_usb_dib0700,dib7000p,dib7000m,dvb_usb,dib3000mc,dibx000_common,dib0070,nvidia

```
cat /proc/drivers/nvidia/version:
```
cat: /proc/drivers/nvidia/version: No such file or directory

```

Big Kahunaca: It didn't work. Thanks for the help though.

Thanks for all your help so far.

---

### Post by XanderCrews on 2009-01-22
Had this problem as well and here's what worked for me:

Assumptions; Using install script from nvidia.com

Through Synaptic, completely remove all linux-restricted-modules packages that you have installed.  Shutdown gdm/kdm and uninstall 
any installed driver via script.  Then install the 180.22 driver via script and restart.  If this works for you it will start again as you would expect, nVidia splash screen and the gdm login screen.

Best of luck.

XC

---

### Post by GCFreak on 2009-01-22
Well, the NVIDIA installer gave me a warning about installing in runlevel 1 (I installed 180.22 it using that last time), so I started runlevel 3 and it starts everything else up and takes me to the desktop, and when I kill the GDM, it takes me to a shell, but it goes crazy, when I do anything with the keyboard it does all sorts of things, and runlevel 1 is the only shell that will work for me. It's wierd, it shouldn't do that should it? How am I going to install the 180.22 drivers in runlevel 3?

---

### Post by GCFreak on 2009-01-22
Ok, nevermind, I found another way to do it, and it works properly now, thanks a million, XanderCrews.

---

### Post by Bpa on 2009-01-22
Install the nvidia drivers with the run script at the real terminal (ctrl-alt-f1) after stopping gnome with a 
```
sudo /etc/init.d/gdm stop
```

Then check in /etc/modprobe.d/ for a file called lrm-video. I moved this file to my desktop, because it was blocking the actual nvidia driver from loading when starting gdm and then using startx. I was highly annoyed with this after spending hours scouring logs for the reason that the nvidia driver wasn't working. I had uninstalled (purged) the previous Ubuntu glx-new nvidia drivers, but I guess the purge missed that particular file.

---

### Post by Ex-Win-User on 2009-01-22
I don't know if this will help. 
This is what I did on my unit running kubuntu intrepid.

I just followed the steps here  [http://www.nvidia.com/object/linux_display_ia32_180.22.html]("http://www.nvidia.com/object/linux_display_ia32_180.22.html")

I downloaded the file then re-login in console mode and run "sudo sh NVIDIA-Linux-x86-180.22-pkg1.run", followed the install process then reboot or run startx

---

