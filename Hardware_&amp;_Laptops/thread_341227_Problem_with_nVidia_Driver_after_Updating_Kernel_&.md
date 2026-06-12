---
title: "Problem with nVidia Driver after Updating Kernel &amp; X.org"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by Flying_OE on 2007-01-18
My system:
P4 with HT enabled
Edgy (newly installed from fresh machine since late last year)
Linux 2.6.17-10-generic #2 SMP i686 GNU/Linux
nVidia GeForce 6200 (DVI + SVGA dual head)

Problem:
I used to use nVidia's official driver (9xxx, the one previous to 9746) with TwinView enabled. Everything was fine though I had to allow the nvidia-installer script to compile a customized version of the kernel module.

I went for holiday during Christmas and returned only this week. Synaptic found some updates (including both the kernel and X.org). I didn't take close look of the changes, and applied the updates.

Ever since then, my system couldn't boot (blank screen whenever X starts). Initially, i suspect that it was due to mismatched kernel version since the kernel was updated. But after doing "nvidia-installer --update," which downloaded the latest 9746 driver and built a new kernel module for me, the same blank screen still awaits me whenever X starts (the X log looks normal though, no error reported). I later also tried Envy 0.8.1 for automatic nVidia driver installation, but exactly the same symptom showed up.

Now I had to revert back to use the open source nv driver (but then I cannot have TwinView now).

Any idea how I can go about fixing this problem? I'm also attaching my xorg.conf. Note that I've commented out the nvidia driver line and replaced it with nv. I can boot into KDE with the nv driver, but nvidia driver will show me a blank screen even all the other options remain the same. (I'm still relatively new to Ubuntu, so if you need additional information/ description, do let me know.) TIA!

---

### Post by Sqwishy on 2007-01-18
I think what happened is when it updated it removed nvidia-glx. You're not the only one with that problem, ecxept i usualy don't update when i noticed somethings being removed.
[http://ubuntuforums.org/showthread.php?t=339311](http://ubuntuforums.org/showthread.php?t=339311)

---

### Post by Flying_OE on 2007-01-18
Thanks for your quick reply. But I double-checked that, and nvidia-installer installs its own version of nvidia-glx driver. So the nvidia-glx package from Synaptic is not necessary (it will be overwritten when nvidia-installer installs the proprietary driver).

(In fact, before using Envy to install nVidia's proprietary driver, I also tried the 877x driver from Synaptic. At that time, I also installed nvidia-glx of the same version. But the symptom was still there unfortunately.)

---

### Post by itsjustarumour on 2007-01-19
Hi Flying_OE, I've been battling with what I think is the same problem for a week ](*,) 

I had Edgy 6.10 with what I thought was the latest kernel version, XGL/Compiz from the official Debian repos, and the NVidia 8776 driver from Tseliot's repos.  This had been running fine for 2 months, but as soon as I installed the NVidia 9746 from the official NVidia site and I booted to my desktop I just got a blank white screen.  My icons were still there behind it btw, I could still click on them, I just couldn't see anything!  :-?   Is this exactly what happened to you?

I removed the driver and tried the official NVidia 9631, but as soon I booted I got a blue screen of death with "Failed to restart X server..."  So I tried going back to the 8776 driver, but still same prob.  If I look at the X server output, it tells me there is a mismatch between the kernel module and the NVidia driver components.

So I went back to the NV driver which still gives me the blue screen when I reboot, but at least I can use ¨startx¨ to get in to my system.

I've been on the offcicial Compiz forums as originally I thought this was Compiz-related, but I don't want to torture the good folks there any more with my noob questions ;)  , especially as this now looks like a Ubuntu issue!  One of the peeps there was kind enough to post up a copy of his xorg.conf file which I tried, but still no joy.

Anyhoo - it looks like latest kernel + official NVidia 9746 driver = permanently damaged Ubuntu!  :(   Unless anyone has any ideas?  :D

---

### Post by Flying_OE on 2007-01-19
Hi, itsjustarumour. No, my problem is not exactly like yours. But anyway, I just solved it after one full week of struggle. Hope my solution can shed some light, and better luck even, help you solve your problem too.

My "blank screen" is basically a black blank screen, though my LCD monitors' backlight was still on. And I could heard that sound of Ubuntu that told me that X thought it was running fine.

After much trial and error, I concluded that latest 9746 driver from nVidia simply doesn't work with the latest Edgy kernel update! I tried the old 8776 driver, tseliot's Envy as well as his 9746 package from his repo, and even downloading 9746 directly from nVidia and built the kernel module using its script. None worked!

Being too desparate, I reverted back to the 9629 (the previous driver release from nVidia, which was also the version I used before Edgy kernel update). Everything worked again automagically! I should have tried this a lot earlier... But after I updated Edgy's kernel, I didn't think much before I ran "sudo nvidia-installer --update" that downloaded and installed 9746 for me.--Tough luck...

To summarize my frustrations expressed above, you can find the simple steps of my solution here:
- Download 9629 driver from nVidia
- sudo apt-get install build-essential pkg-config xserver-xorg-dev
- If you have linux-restricted-modules installed, add "nv" into the DISABLED_MODULES list in /etc/default/linux-restricted-modules-common.
- sudo apt-get --purge remove nvidia-glx nvidia-settings
- Return to console login if you were in X
- sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
- Follow the script to build your own nvidia kernel module
- Edit /etc/X11/xorg.conf appropriately (you may just try using the version you used prior to kernel update)
- Reboot

Hope this helps.

---

### Post by Zer0Nin3r on 2007-01-21
I had the same problem in that my xserver was crashing after I installed the *recommended* updates _after_ installing the proprietary drivers from nVidia.  I basically did a wipe and clean install and retraced my steps with the exception of updating the xserver and xorg.  Hope that gives you some insight.  Although I fear you have files you don't want to lose.

Also, when I was having this problem, the installer would not work and would run into errors when trying to re-install the drivers.  Hence I just decided to wipe the drive and start all over again.

---

### Post by JayTee on 2007-01-24
That's really odd. I had a similar problem with the kernel updates around Christmas that broke my Xserver. I just ran Envy and it reinstalled the 9746 version driver from Nvidia. I've been running that with Beryl 0.1.4 for over a month now with no problems except for that update and it only took a few minutes to fix. I don't really think it's the 9746 driver that's causing problems. Perhaps something else is preventing the Envy script for properly updating your drivers.

---

### Post by Flying_OE on 2007-01-26
As a matter of fact, I also found it really weird. But besides the Envy script, I also tried manual download/installation of the 9746 driver--still no joy. And all my problems went away when I revert back to 9629. (I also tested 9631, same problem as 9746. So I suspect that it is some update in nVidia driver introduced at 9631 that actually broke my setup.)

---

