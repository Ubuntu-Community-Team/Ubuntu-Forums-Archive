---
title: "Getting a New Laptop"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by chronusdark on 2006-06-19
I just ordered a Dell XPS M1210 and i was wanting to know if anyone has had any problems with dapper on this computer

thanks

---

### Post by tigrux on 2006-06-19
It seems you will be one of the first owners of this laptop.

We'll be waiting for your report.

---

### Post by chronusdark on 2006-06-19
i will be happy to give it

---

### Post by billyfoxtrot on 2006-08-09
chronusdark,

Did you get your XPS M1210 yet?  I'm thinking of getting one, but I want to know that everything works with Ubuntu first.  Let us know!

---

### Post by stryderjzw on 2006-08-10
Me too, thinking of getting this... keep us informed!

---

### Post by freed0m on 2006-08-23
Hello, first post here.
 
I have installed dapper in my m1210. Everything just fine. After the install. the screen resolution was 1280 x 760. But with the help of 915resolution utility now its 1280 x 800. The only problem i have its with the wireless.
Trying to solve ASAP.

Cheers.
Daniel

---

### Post by sfitzjava on 2006-08-29
I got the WiFi working by installing the ipw3945 packages.  They don't have the firmware installed by default.  After I installed and it works great with the Gnome desktop.

However I have 2 issues.  I have the Nvidia graphics, no camera, and am unable to get the microphone to work.  
The other is the suspend2ram doesn't work, and suspend2disk is not 100%. :(

-Shawn

---

### Post by ubuntu_demon on 2006-09-08
I might be interested in this laptop. Are you guys happy with your purchase ?

Here's the thread about "Help me find a good laptop" :
[http://www.ubuntuforums.org/showthread.php?t=247158](http://www.ubuntuforums.org/showthread.php?t=247158)

Here are some links to information about this dell laptop :

[https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1210](https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1210)
[http://g33k.wordpress.com/2006/07/20/the-dell-xps-m1210-a-mini-review/](http://g33k.wordpress.com/2006/07/20/the-dell-xps-m1210-a-mini-review/)
[http://toufeeq.blogspot.com/2006/07/linux-on-dell-xps-m1210.html](http://toufeeq.blogspot.com/2006/07/linux-on-dell-xps-m1210.html)

from [http://imaging.ugent.be/mr/Suse/suse-m1210.html](http://imaging.ugent.be/mr/Suse/suse-m1210.html) :

> 
After the installation of the NVIDIA driver, Suspend to RAM worked well after setting SUSPEND2RAM_FORCE="yes" in '/etc/powersave/sleep'.


Can anyone confirm whether this works on Ubuntu as well ?

More about suspend from [http://imaging.ugent.be/mr/Suse/suse-m1210.html](http://imaging.ugent.be/mr/Suse/suse-m1210.html) :

> 
Suspend to disc with the original kernel 2.6.16.13-4-smp works quite well, but during suspend the snd_usb_audio module can not be unloaded, and this causes USB not to work after resume and kmix seems to hang after resume. After looking in /var/log/messages, I added the module uhci-hcd to be unloaded before suspend and the be reloaded upon resume: UNLOAD_MODULES_BEFORE_SUSPEND2RAM="uhci-hcd"

This at least restores the functionality of the USB ports (mouse and USB-disc). Executing 'killall kmix; kmix' with 'alt+F2' is sometimes necessary. I cannot figure out why that is so....(any help welcome)

Follow-up:

20060721 - Suspend problems:

After a recommended kernel upgraded from 2.6.16.13-4-smp to 2.6.16.21-0.13-smp, this broke the good working S3 and S4 states. A working S3 state could be restored as follows:

I installed the Nvidia Driver(s) by adding [ftp://download.nvidia.com/novell](ftp://download.nvidia.com/novell) as an installation repository as described in [http://www.suse.de/~sndirsch/nvidia-installer-HOWTO.html#](http://www.suse.de/~sndirsch/nvidia-installer-HOWTO.html#), and installed the packages x11-video-nvidia and nvidia-gfx-kmp-smp with YAST.

I then followed advice from [http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO), to enable NvAGP in /etc/X11/xorg.conf and blacklist the intel_agp module. I also tried 'noapic' as kernel parameter upon boot, but it proved to be unnecessary.

Issue for S3: Unfortunately, I now have a kbd problem after resume from S3, the keyboard acts erratic. It behaves as if it has lost the keyboard delay in some instances only. Even trying to correct with


---

### Post by Spif on 2006-09-08
How good is the battery life with Dapper?

---

### Post by sfitzjava on 2006-09-08
On Battery Usage:
I'm getting about 3hrs on the standard battery.  I haven't plugged in my big battery to see, but I would imagine it should get about 5 or 6hrs.

On the Suspend2Ram from the Suse instructions:
Nope, by putting in the Nvidia driver did not help.  It still puts the screen to an off mode (can't see what happens) then the HD light blinks every so often, but never goes into suspend.

On Suspend2Disk:
I've had that going for a while.  However it will work several times then hang.  It took about 48sec to restart from a hibernated state, and about 53sec to boot cold.  So for all the issues, I would say don't bother with it.
Or at least till it is stable.

However I installed the IRQbalancer which helped my performance.  The thing is you have to unload and reload that when doing a suspend.
You need to add a command script in the /etc/acpi/suspend.d and in the /etc/acpi/resume.d directories.  Make it the first thing that is unloaded.

One last point.  Most of the Suse instructions for S2R and S2D are based on the KDE, and not the Gnome.  So they are using powersaved and not the gnome power management services.  There are major differences in these two methods, so ubuntu is more difficult to configure for than kubuntu.

YMMV.

-Sfitz

---

### Post by sfitzjava on 2006-09-08
Okay having just posted saying I couldn't do Suspend2Ram, I found a few clues and have successfully suspended 2 ram a couple times. 

I added the following line to the xorg.conf
  Option   "NvAgp"  "0"

in the Section "Device" for the Nvidia driver.

(I tried NvAgp "1" and that failed.)

However it worked twice, and the startup on the 3rd time the mouse could not trigger any of the UI.   That may have been because I left my USB mouse and (maybe more importantly) the USB sound card.  (I have a AHS302USB sound card because I can't get the built in mic to work which I need for Skype.)

So some success.   Also I should note that the NvAgp can also support a value of "2" and "3", so there may be better options using one of those.

YMMV

regards
-sfitz

---

### Post by ubuntu_demon on 2006-09-09
> **sfitzjava said:**
> Okay having just posted saying I couldn't do Suspend2Ram, I found a few clues and have successfully suspended 2 ram a couple times. 

I added the following line to the xorg.conf
  Option   "NvAgp"  "0"

in the Section "Device" for the Nvidia driver.

(I tried NvAgp "1" and that failed.)

However it worked twice, and the startup on the 3rd time the mouse could not trigger any of the UI.   That may have been because I left my USB mouse and (maybe more importantly) the USB sound card.  (I have a AHS302USB sound card because I can't get the built in mic to work which I need for Skype.)

So some success.   Also I should note that the NvAgp can also support a value of "2" and "3", so there may be better options using one of those.

YMMV

regards
-sfitz
> 
After the installation of the NVIDIA driver, Suspend to RAM worked well after setting SUSPEND2RAM_FORCE="yes" in '/etc/powersave/sleep'.


I don't have a laptop. But does this (or something similar) work ? 

see this blog post :
[http://imaging.ugent.be/mr/Suse/suse-m1210.html](http://imaging.ugent.be/mr/Suse/suse-m1210.html)

and my previous post here :
[http://www.ubuntuforums.org/showpost.php?p=1476707&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1476707&postcount=8)

---

### Post by gregkiwman on 2006-09-09
Hello ! ;) 
I will buy the Acer Aspire 9804WKmi in the following two weeks and really would like to install Ubuntu 6.06 on it. 
Does anyone know if the Dapper version can be displayed on a 20.1 inch screen with a 1680 x 1050 pixel resolution ?

The laptop also has two hard drives with windows pre-installed: is the usual dual-boot installation possible then, or should I use one HD for windows and the second for Ubuntu ?

Cheers, 

Greg.

---

### Post by stryderjzw on 2006-09-16
I'm having difficulty getting my internal mic and camera working on my XPS.

Any suggestions?

---

### Post by chronusdark on 2006-09-18
sorry on the lateness but i have been happily using my xpsm1210 for about 2 months now and dapper runs fine on it, i have had 0 hardware issues wireless works flawlessly if you put network-manager on as for suspend2ram i have not used this feature as i like to just shut my laptop down
after the most recent updates tho i have noticed that with the default settings the shutdown just goes blank and shows no splash but it still shuts down fine i figured out its something to do with my vga= option so i need to discover the best option for it

i didnt get the package with the camera and mic so i cannot test that

but all in all the m 1210 is an awesome machine for ubuntu

---

### Post by stryderjzw on 2006-09-18
Thanks for replying!

I'm loving the M1210 for Ubuntu.  Very smooth.

I've managed somehow to get mic and camera working, but camera only for Ekiga.

This machine is a beast.

I did notice that I get a blank screen when I shutdown too.  Also, my nvidia settings sorta disappear when I installed XGL.

Weird. :D

---

### Post by dante00001 on 2006-10-05
i just bought a M1210 im considering installing ubuntu in a dual boot setup. i was just wondering how you got the camera to work. any info would be greatly appreciated.

---

### Post by stryderjzw on 2006-10-05
> **dante00001 said:**
> i just bought a M1210 im considering installing ubuntu in a dual boot setup. i was just wondering how you got the camera to work. any info would be greatly appreciated.

I believe I followed the instructions at the links provided in this thread.

[http://ubuntuforums.org/showpost.php?p=1476707&postcount=8](http://ubuntuforums.org/showpost.php?p=1476707&postcount=8)

I think this one..  I can't remember exactly....

---

