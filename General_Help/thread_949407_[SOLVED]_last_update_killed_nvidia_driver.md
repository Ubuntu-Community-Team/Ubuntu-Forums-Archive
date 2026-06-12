---
title: "[SOLVED] last update killed nvidia driver"
date: 2008-10-16
forum: General Help
---

### Post by eragon100 on 2008-10-16
Yesterday I installed the latest kernel packages and continued to use the computer for 6 more hours. Restarted computer this morning, nvdia driver doesn´t work anymore. Removed and reinstalled with envy, now it loads but 3d still doesn´t work, "GLX module not loaded""

HELP!!

---

### Post by sparky-steve on 2008-10-16
Hello,

My nvidia card stopped working with the kernel update yesterday too, as I'm sure did many others; I've never had much luck with the ready-to-go nvidia drivers and have always compiled my own.

[http://www.nvidia.com/object/linux_display_ia32_177.80.html](http://www.nvidia.com/object/linux_display_ia32_177.80.html)

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/177.80/NVIDIA-Linux-x86-177.80-pkg1.run
```

You'll need to install some dependancies if you've never compiled your own nvidia driver; these are my notes which work for me - your mileage may vary.

(all done in the terminal/konsole without X running, and assuming your kernel is 2.6.24-21) (in gnome, when you get to the login prompt, press CTRL-ALT-F2 and log in, then sudo killall gdm)

```


cd /etc/X11
sudo cp xorg.conf xorg.conf.backup.16102008
sudo apt-get install binutils build-essential linux-source gcc make pkg-config xserver-xorg-dev libc-dev linux-headers-2.6.24-21

comment out the following two lines in  /lib/modules/2.6.24-21-generic/modules.alias :-
#alias char-major-195-* nvidia_legacy
#alias pci:v000010DEd*sv*sd*bc03sc00i00* nvidia_legacy

cd /root/
wget wget http://us.download.nvidia.com/XFree86/Linux-x86/177.80/NVIDIA-Linux-x86-177.80-pkg1.run
sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
```

There are a few basic questions - just let it do what it wants.

I hope that helps you.... Sorry if not!

Edit: let me know if you do run into problems, and if I can assist I will, gladly.

---

### Post by eragon100 on 2008-10-16
> **sparky-steve said:**
> Hello,

My nvidia card stopped working with the kernel update yesterday too, as I'm sure did many others; I've never had much luck with the ready-to-go nvidia drivers and have always compiled my own.

[http://www.nvidia.com/object/linux_display_ia32_177.80.html](http://www.nvidia.com/object/linux_display_ia32_177.80.html)

```
wget http://us.download.nvidia.com/XFree86/Linux-x86/177.80/NVIDIA-Linux-x86-177.80-pkg1.run
```

You'll need to install some dependancies if you've never compiled your own nvidia driver; these are my notes which work for me - your mileage may vary.

(all done in the terminal/konsole without X running, and assuming your kernel is 2.6.24-21) (in gnome, when you get to the login prompt, press CTRL-ALT-F2 and log in, then sudo killall gdm)

```


cd /etc/X11
sudo cp xorg.conf xorg.conf.backup.16102008
sudo apt-get install binutils build-essential linux-source gcc make pkg-config xserver-xorg-dev libc-dev linux-headers-2.6.24-21

comment out the following two lines in  /lib/modules/2.6.24-21-generic/modules.alias :-
#alias char-major-195-* nvidia_legacy
#alias pci:v000010DEd*sv*sd*bc03sc00i00* nvidia_legacy

cd /root/
wget wget http://us.download.nvidia.com/XFree86/Linux-x86/177.80/NVIDIA-Linux-x86-177.80-pkg1.run
sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
```

There are a few basic questions - just let it do what it wants.

I hope that helps you.... Sorry if not!

Edit: let me know if you do run into problems, and if I can assist I will, gladly.

I always do that to update the driver, it's very easy, I just didn't think it would be necessary now, I am going to try this right away. Thanx for the help! :wink:

---

### Post by sparky-steve on 2008-10-16
> **eragon100 said:**
> I always do that to update the driver, it's very easy, I just didn't think it would be necessary now, I am going to try this right away. Thanx for the help! :wink:

Every time the kernel changes, you have to recompile the nvidia driver.

Fingers crossed you'll have it working shortly!

Steve

---

### Post by eragon100 on 2008-10-16
I removed the envy-installed driver and installed the nvidia package, everything is working great again! thanx! :popcorn:

---

### Post by sparky-steve on 2008-10-16
Brilliant! Glad it worked for you.

Perhaps you could edit your subject and just add [solved] to the end of the existing subject? Helps others find a solution in the future ;-)

Steve
:guitar:

---

