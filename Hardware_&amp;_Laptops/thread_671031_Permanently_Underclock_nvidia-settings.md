---
title: "Permanently Underclock nvidia-settings"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by jenra on 2008-01-18
Hello,
I'm a college student running Ubuntu 7.10. I am trying to maximize the battery life of my laptop (Asus A8Js) because I am on the go constantly for a good deal of hours at a time. I have used powertop to minimize the power usage of all of the components inside of my laptop except for the nVidia Go 7700. 
I have used the following sites to try and permanently underclock the video card's core and memory speeds:
[http://gentoo-wiki.com/HOWTO_nVidia_Drivers](http://gentoo-wiki.com/HOWTO_nVidia_Drivers)
[ftp://download.nvidia.com/XFree86/Linux-x86/nvidia-settings-user-guide.txt](ftp://download.nvidia.com/XFree86/Linux-x86/nvidia-settings-user-guide.txt)
Using these guides I have tried the following:
Enabling "Coolbits" in xorg.conf, this seems to work temporarily, but the effect is not permanent.
NVClock utility, again works, but only temporarily.
Creating a .xinitrc file that reads:
    nvidia-settings --config=~/.my-nv-settings-rc &
    ./etc/X11/xinit/xinitrc
Creating my own .nv-settings-rc with the new clock speeds, the nvidia-settings overwrites this file.
I have had absolutely no luck thus far in underclocking, and am looking for new ideas and approaches. Thanks in advance for any help offered!

---

### Post by jeffus_il on 2008-01-18
Did you do this?

> The overclock settings are not wrtten to the ~/.nvidia-settings-rc file by default and therefore the settings will not survive restarting X. To fix this, quit nvidia-settings if it is running, open ~/.nvidia-settings-rc in a text editor and add the following lines: 
    [SIZE=-1]**File:** .nvidia-settings-rc: Additional attributes to preserve overclock settings[/SIZE]     GPUOverclockingState=1
GPU2DClockFreqs=625,805
GPU3DClockFreqs=625,805


  

---

### Post by jenra on 2008-01-18
jeffus_il,
Yes, I did try doing this, however, the interesting thing is that nvidia-settings not only overwrites the .nvidia-settings-rc, but also the settings file I created: .my-nv-settings-rc, completely getting rid of my underclocking statements. 
I just realized there are backup files in the home folder, .my-nv-settings-rc~ and .nvidia-settings-rc~. I'll back these files up under a different name, delete them, and see if that is a successful approach, perhaps it will stop overwriting the settings files.
In the mean time, if anyone else has any solutions or has had any success with this in the past, your approaches would be greatly appreciated.

EDIT: Okay, so I just tried the method above (delete the backup files, edit .nvidia-settings-rc with the underclocking statements, but with no success. What happens is as follows:
1) I make sure nvidia-settings is closed
2) I edit the .nvidia-settings-rc with the following (and also assuming that the placement of these lines doesn't matter)
    GPUOverclockingState=1
    GPU2DClockFreqs=625,805
    GPU3DClockFreqs=625,805
3) I start up nvidia-settings, hoping that it will load from the customized file
4) I click on PowerMIzer to find that nothing has changed
At this point, a new .nvidia-settings-rc~ has been created, which is apparently the backup file, so I wonder if that has to do with anything.
The other interesting point is that the .xinitrc I made (see the first post) isn't functioning properly, or I don't know how to use it properly (which is more likely). It should be starting nvidia-settings with my own configuration file which includes the underclocking statements. Unfortunately, this isn't the case at all, and I actually can't really tell what's going on.
Again, if anyone has had success with this endeavor, please let me know, thank you in advance.

---

### Post by jenra on 2008-01-19
*bump
I found that the clock settings I was using were not in the allowed range for overclocking this card, so I changed the numbers so they fit in properly into the allowed range, but sitll no luck when looking at the powermizer tab in nvidia-settings. 
Any ideas, anyone?:(

---

### Post by Maulwuff on 2008-02-09
try these links:

[http://aldeby.wordpress.com/2007/12/21/nvidia-powermizer-powersaving/](http://aldeby.wordpress.com/2007/12/21/nvidia-powermizer-powersaving/)
[http://aldeby.wordpress.com/2007/12/22/enable-nvidia-coolbits-frequency-tuner/](http://aldeby.wordpress.com/2007/12/22/enable-nvidia-coolbits-frequency-tuner/)

i clocked my 6200 go down to the settings given by powermizer in state 0, (on 3D clock freqs, 2D is already on lowest settings)
if it persists after reboot -- don't know yet.

---

### Post by buckeliger on 2008-03-17
i have similar problems with my geforce 6150 with the latest stable nvidia drivers and hardy heron. 

whenever i try to change the frequency in nvidia-settings, the control jumps back to the original value. my GPU gets up to 100°C; that can't be healthy!?

---

### Post by h4mx0r on 2008-04-13
100C is horrible, I reseated the fan on mine with some new thermal paste and noticed a big improvement but now its acting up again and I think it would be best to just underclock it. Mine usually resets xorg or crashes the 3d app if it gets near 70C, it usually runs at about 58C though unless its under load.

---

### Post by idomagic on 2008-06-04
Anyone had some success with this?

I just had to replace the vga card in my server, bought the cheapest passively cooled one I could find, which happened to be an agp, msi fx5200. Which also happened to be a hot little bugger.

Since the server is actually headless, I figured I could underclock it quite alot (coolbits allowed me to underclock it to 62mhz(!) from 250), but I don't want to be forced to load the gui just for the underclock. Surely it has to be possible to apply on startup?

edit: maybe simply doing nvidia-settings --assign="GPU2DClockFreqs=<gpuclock>,<memclock>" at startup would work?
edit2: indeed, that would probably work, found this howto: [http://ubuntuforums.org/showthread.php?t=254397](http://ubuntuforums.org/showthread.php?t=254397)

---

### Post by aldeby on 2008-06-27
This is just a note to tell you that backup file ending with ~ are actually automatically created by gedit once you edit the regular file. They are not made by nvidia drivers. 

I haven't figured out how to permanently set frequencies yet (even though I guess we have to set them in xorg.conf, not in userspace files ($HOME/.), 
however you can start by forcing the lowest frequencies used by Power Mizer

[http://ubuntuforums.org/showthread.php?p=5265688](http://ubuntuforums.org/showthread.php?p=5265688)
[http://aldeby.org/blog/index.php/nvidia-powermizer-powersaving.html](http://aldeby.org/blog/index.php/nvidia-powermizer-powersaving.html)

---

