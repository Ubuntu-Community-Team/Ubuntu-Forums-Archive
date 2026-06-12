---
title: "nVidia geForce 8800 GTS problems"
date: 2012-11-15
forum: Hardware
---

### Post by ARooster on 2012-11-15
I've been using Ubuntu since 9.10 and have stuck with it through the shift to Unity. I am currently using 12.10 64 bit. Due to various problems and clutter I've just performed another fresh install of 12.10 to start from scratch.

The default graphics driver is the Noveau display driver. Using Additional Drivers menu in the Software Sources application I moved the driver to the nVidia current proprietary tested driver. After reboot, the screen goes into low res mode with no Dash side pannel or any other bars, just the desktop can be seen. Ctrl-Alt-F2 turns the screen black with no prompt and Ctrl-Alt-F7 does not bring the desktop back. The RMB on the desktop works, where I found my way into the settings and set it back to the Noveau display driver.

Ctrl+Alt+T will also bring up the terminal emulator.

I have tried installing the recent nVidia driver from the nVidia website. After rebooting the Unity bar, start button, clock etc did come up, but in a low resolution mode that was also very sluggish. I've had the same with both the 64 and 32 bit versions of Ubuntu 12.10, the NVIDIA drivers were 304.64, 64 and 32 bit, respectively.

Using Oracle's VirtualBox, the window switcher function of the sidebar (the 2nd click of the icon thing) locks up the graphics for several seconds (while streaming sound may be running in the background for awhile until it, too, stops. It resumes after some 20 seconds but will lock up again when the same window switcher function is used.

It may be noteworthy that running KDE Plasma desktop on Ubuntu, I did not have any such stability issues.

Could anyone point me in the direction of a solid and working graphics driver or a fix of this problem? Thanks :)

---

### Post by NikTh on 2012-11-15
Hi , 
to revert back to nouveau driver , open a terminal and do 
```
sudo apt-get purge nvidia-*
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall nvidia-common xserver-xorg-video-nouveau
sudo dpkg-reconfigure xserver-xorg
```Then reboot your system with this command
```
sudo reboot
```Now , about the closed source driver , I had this problem too. None of the drivers provided in software-sources worked for me. The only driver that worked (Installed recently 2 days ago) is the Beta 310.14. Be informed here that Beta is Beta. You know. But for me is the only driver I was able to install. 
I tried everything (installed linux-source , headers-generic .. etc) but nothing seemed to work for me. 
Then decided to download the Beta driver , you can find it here for 64bit Ubuntu => [http://www.nvidia.com/object/linux-display-amd64-310.14-driver.html](http://www.nvidia.com/object/linux-display-amd64-310.14-driver.html)
but the procedure is a little different . 

If you want to test it  and you want guide for the procedure , let me know. 

I didn't understand exactly the problem with VirtualBox , but restore  first your Desktop Environment and we can talk about this later.


Thanks

---

### Post by oldfred on 2012-11-15
Only with 12.10, I had to install the headers before getting nVidia to install correctly. I have the 9600GT and I used nvidia-current-updates which was the middle one version wise.

[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic

then install nVidia. There now are several versions on repository.

May want nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by ARooster on 2012-11-15
Oh, thanks, NikTh and oldfred! I am going to try it now. NikTh, regarding VirtualBox, I suspect that finding a stable nVidia driver will solve this problem, too. I think it's all compiz-related (as I said, no issues with KDE Plasma desktop whatsoever).

I'll try out the suggested solutions and get back to you with the results :) Thanks a lot :)

---

### Post by ARooster on 2012-11-15
oldfred, the nvidia-current and nvidia-current-updates were a miss. It's back to Nouveau.

NikTh, I tried setting up the driver you suggested but with no luck. I stopped the xserver, changed downloaded file flag to executable and executed it. I got the same problem... a desktop with no Unity. Also, after one of my reboots compiz complained about shutting down unexpectedly.

---

### Post by ARooster on 2012-11-15
After a bit of poking around I discovered I was stuck on Nouveau for some strange reason, the settings didn't want to move. A bit of poking around later I've managed to remove and restore everything and it actually does seem it was the linux header files issue.

a
```
sudo apt-get update
sudo apt-get install linux-headers-generic
sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-current
sudo reboot
```
later I am up and running. I have yet to see what's going on when I go through the motions with VirtualBox etc, however. Thanks for the help, chaps!

---

### Post by Frogs Hair on 2012-11-15
Glad you have it working. I am running the experimental 304.48 64 bit on my 8 series card and It runs great. Nvidia current was the worst performer of the four available drivers and it is the only tested one of the three Nvidia drivers.

---

### Post by ARooster on 2012-11-16
Right, unfortunately, the stability issues reoccured when running Thunderbird, VirtualBox, Firefox and VLC Player at the same time.

I am "solving" this issue by moving back to Precise. I think I'll wait for 13.04, this graphics issue is just too much hassle to be worth the few minor improvements 12.10 offers over 12.04.

---

