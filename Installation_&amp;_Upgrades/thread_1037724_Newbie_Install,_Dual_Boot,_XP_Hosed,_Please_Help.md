---
title: "Newbie Install, Dual Boot, XP Hosed, Please Help"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by Razmear on 2009-01-12
I've been at this about 20 hours now and am finally posting for help, so forgive any rambling on in this post as I want to cover all the basics. 

Firstly, I am on an XP SP3, HP Pavilion 780N, which was just set up to dual boot with Ubuntu 8.10 
The PC has 3 hard drives & a DVD Rom. The 3rd hard drive (18Gig) was wiped clean for the Ubuntu install and the other two drives which are used for XP were not touched by the install process, except by the bootloader. 
The Ubuntu install went fine with the exception of working nicely with my NVidia MX440 GeForce video card, which is still a problem as I'm stuck at very low resolution, but that's not my main concern at the moment. 

I finally decided to take a break and boot back into XP to check my mail and stuff, and when I chose XP from the boot menu I get a message that HP System Recovery is running, then a blue screen of death saying the system has been stopped. 
Now I really do want to get a Linux system up and running and be done with MS, but I have lots of stuff over there that I'm not quite ready to part with yet, and would really like to be able to get back into XP again. 

I can access the XP drives thru the file manager in Ubuntu, so there is some hope of at least getting my data recovered in the event of a total loss of access, but if anyone can point me in the right direction of getting the XP booting to work again, it would be really appriciated as my brain is about fried at the moment. 
Also, I've been reading about how to get the Nvidia drivers working for about the past 8 hours so if anyone has any hints on that it would be great too. I'm stuck at 800x600 res on the NEC monitor, but the TV out lets me choose any of several resolutions, which would be great if the TV wasn't 12 feet away (or if I had much better eyesight). 
Also for some reason whenever I run the NVidia Setting Tool it sets my monitor refresh rates to 429234556 Htz in the xorg.conf file which requires a manual edit after being dumped into low rez warning mode and choosing to troubleshoot and edit the conf file. (yeah, been having a fun day)....

My first goal is to be able to get back into XP, second goal is to get this video working properly so I can start using Ubuntu. 

Thanks in advance for any help and I'll be up pulling my hair out if you need any system logs or error messages. 

eb

---

### Post by kranny on 2009-01-12
please post the output of:
```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by Razmear on 2009-01-12
Thanks,
I did some more panic googling and found the problem. 

Switching /boot/grub/menu.lst 's XP section to 0,1 from 0,0 fixed the problem. 0,0 is the recovery partition on this POS HP box. Also choosing the XP Whisper Personal option will load XP. (discovered by accedent after trying 1,1 and getting an error)

I'm over in XP land now looking for solutions to the Nvidia problems. The XP boot part of my problem is solved but if anyone has any good pointers on getting a NVidia GeForce MX440 video card working on this system, it would be a great help. It's an older 64meg card, but it has an SVHS out that goes to my TV for watching videos and stuff, so I'd like to hang on to it. 

Currently I'm locked in 800x600 resolution on my monitor and can select way to many resolution options for the TV. Any editing of the conf file thru the nvidia setup app hoses the refresh rates in the conf file (as described in the op), and several manual edits have done no good trying to force a higher resolution. 
Going to the default driver gives me a choice of 8x6 or 6x4 rez, so that's no help either. 
Driver version 96.x is what is being used at the moment. 

Thanks again, back to googling.....

eb

---

### Post by damphoud on 2009-01-12
Try updating to the latest stable driver, 180.xx. Check out this post: 
[http://ubuntuforums.org/showthread.php?t=990978&highlight=180](http://ubuntuforums.org/showthread.php?t=990978&highlight=180)

---

### Post by balaknair on 2009-01-12
The newer nVidia drivers might help.
Try using Envy to automatically get the latest drivers.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Razmear on 2009-01-12
Thanks, I'm gonna flip back to Ubuntu and try the 180 version. 
Noticed in the fix list: 
Fixed a problem parsing the monitor sync range X config file options. 
which is definitly one of the bugs I was hitting, so I'll give it a shot. 

Will post Joy/No Joy after loading. 

eb

---

### Post by damphoud on 2009-01-12
> **Razmear said:**
> Thanks, I'm gonna flip back to Ubuntu and try the 180 version. 
Noticed in the fix list: 
Fixed a problem parsing the monitor sync range X config file options. 
which is definitly one of the bugs I was hitting, so I'll give it a shot. 

Will post Joy/No Joy after loading. 

eb

Good Luck!:lolflag:

---

### Post by Razmear on 2009-01-12
No Joy,
The install stated my card is not supported by the 180 driver set and would be ignored, says to use the 96.43.xx drivers which are apparently still screwed up. 
Back to hacking at the config file I guess. 

eb

---

### Post by Partyboi2 on 2009-01-12
Maybe this will help.
[http://kmandla.wordpress.com/2008/11/04/compiling-nvidia-driver-964309-on-intrepid-2627-7/](http://kmandla.wordpress.com/2008/11/04/compiling-nvidia-driver-964309-on-intrepid-2627-7/)

---

### Post by Razmear on 2009-01-12
Thanks Parti, I'll give that process a shot when I wake up in the afternoon. Brains about toast right now. 

I think most of my problem is with the Nvidia Server Settings applet and not so much the driver. 

Here is an example of what that applet is doing when I try to use it: 

From xorg.conf before using the applet: 
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Then after using the applet to switch to 'twinview' (or make any other changes):
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "@@@"
    HorizSync       4294967.0 - 0.0
    VertRefresh     4294967296.0 - 0.0
    Option         "DPMS"
EndSection

If there was another util for setting up the nvidia options that might help a bit, as everytime I use this one it just hoses things up more. 
I've also tried copying other examples of the .conf file with no joy in getting this bugger to work. 
Looks like I might have to break down and give newegg $15 for a new video card, :)

eb

---

### Post by Partyboi2 on 2009-01-12
If you have the driver installed then try using nvidia settings (system>admin>Nvidia Server x Settings) to change the resolution. If its not in the menu then you can install
```
sudo apt-get install nvidia-settings
```

---

### Post by Elfy on 2009-01-12
Hi - can you open synaptic and search for nvidia-glx-96 - tell us what version you have installed please.

It could be 96.43.05 or 96.43.09

Also - what was the last method you used to install the driver - envy or hardware drivers?

---

### Post by Razmear on 2009-01-12
Parti,
I've been using the Nvidia Server X Settings to try and change the rez. It only offers 8x6 as an option, and hoses the refresh rates (as posted in the last post on page 1) whenever it writes to the config file. I'm trying to see if there is a newer version of the Server X Settings applet that is fixed without getting the 180 driver that won't work on my card. 

Forest,
96.43.09 is the driver version I'm running. It's been istalled thru Envy and via command line a few times each. 

and knowing this will be asked sometime after I've passed out and am having nightmares about this evening, here is my complete current xorg.conf file: 

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Mon Oct 27 14:37:20 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

--

Its about 6am here, and I really should be out cold by now....
eb

---

### Post by Elfy on 2009-01-12
Ok - the good news - that card does work on Intrepid, I had one until recently, I found my old xorg.xonf which I had a tv working off as well.

I would start again - remove the driver using envy and make sure that hardware drivers doesn't see it as enabled, you'll need to reboot after envy removes it - check then that hardware drivers say's it's not enabled.

Now make sure that your system is completely updated

```
sudo apt-get &&sudo apt-get upgrade
```

Now use Hardware drivers to install and enable the driver - reboot.

Run the update and upgrade command again, if there is an nvidia update don't bother with the next step.

[indent]_The Next Step_
When I was using the card there were a couple of proposed updates for it - I don't know whether they have been released yet, so we can check.

Open software sources - go to the update tab and enable proposed - not backports, close that and when it wnats to reload let it do so.

You should get a notification that there are updates available - _do not install them._

Check down the list and look for any nvidia updates, if there are any - untick everything except the nvidia ones and let them install.[/indent]

Go back to Software sources and disable the proposed updates and reload.

Now run nvidia-settings

```
gksu nvidia-settings
```

concentrate on setting up the monitor first before you get to the tv. Once that is setup - restart X - logout or ctrl+bkspc. You should have the resolution set on the monitor now, go back to nvidia-settings for the tv.

Those steps are the ones I used to get my card working on Intrepid.

---

