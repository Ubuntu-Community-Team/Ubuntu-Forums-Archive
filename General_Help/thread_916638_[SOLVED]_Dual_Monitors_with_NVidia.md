---
title: "[SOLVED] Dual Monitors with NVidia"
date: 2008-09-11
forum: General Help
---

### Post by Iwneferi on 2008-09-11
I am having great difficulties getting my dual monitor display to work. Both monitors work on startup, but once ubuntu loads, the second one disappears and cannot be found. When I tell "Monitor Resolution Settings" to "Detect Displays" absolutely nothing happens. It does not appear to be trying to do anything even.

I've installed the hardware drivers for my nVidia card, as well as Compiz, and I have all of the advanced desktop effects, on my one monitor.

I tried to download and install the nVidia driver for linux, following the instructions on their webpage. ([http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html)) I successfully downloaded the driver, but when I try to install it, it says:

sh: Can't open NVIDIA-linux-x86-177.13.pkg1.run

I also tried to follow the HowTo on the ubuntu webforums ([http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)).

When I am following the preparation instructions:

"Now, we always want to have a clean slate, because it makes the work much easier, and there is less of a chance that some other arbitrary item will mess this whole thing up.
So, unplug all your monitors except for one, then execute the following command:

sudo dpkg-reconfigure xserver-xorg

Just hit enter for the most options, though if you have the binary drivers installed, you might want to select that. This code will generate a new, clean, standard xorg.conf file for us to work on."

I get partway through the reconfiguration, but the terminal screen freezes when I get to the section on keyboard configuration. As such, I have not tried to finish following the directions for my dual monitor setup.

Any suggestions??????


Thanks in advance!

---

### Post by ad_267 on 2008-09-11
Use nvidia-settings.

Open up a terminal (Applications - Accessories - Terminal) and enter:
```
sudo apt-get install nvidia-settings
gksu nvidia-settings
```

Then enable the second monitor with TwinView and set the resolutions then click "Save to X configuration file."

You can use "sudo dpkg-reconfigure -phigh xserver-xorg" to set the configuration to defaults without going through the options and then enable the drivers with the Hardware Drivers tool in Ubuntu.

---

### Post by Iwneferi on 2008-09-11
Ok,

When I typed in "gksu nvidia-settings" I got a prompt that said "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia xconfig' as root) and restart the X server."

How do I do this?

~Many Thanx

---

### Post by ad_267 on 2008-09-11
In the terminal you can enter:

```
sudo nvidia-xconfig
```

But you shouldn't have to do that. If you enable the nvidia drivers from System - Administration - Hardware Drivers and log out and back in then the drivers should be enabled.

---

### Post by Iwneferi on 2008-09-11
I have long since enabled the nVidia Harware Drivers. They allowed me to do Advanced Desktop Effects. But I still need to get my dual monitors working. When I typed in your prompt "sudo nvidia-xconfig" I received the response:

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


And then I still get the same error for the nVidia Settings.

I'm assuming that this is from some of the preparation steps I followed trying to do the "How To" I mentioned earlier...

---

### Post by ad_267 on 2008-09-11
You need to restart your computer for the new drivers to be used.

---

### Post by Iwneferi on 2008-09-12
I haven't gotten any drivers in the last week, and I restart my computer several times a day.

---

### Post by michaelkahl on 2008-09-12
I've had the best success with the EnvyNG program.  You can install it from synaptic package manager.  The program is available from Applications > System Tools
It's a simple gui that allows you to uninstall or install Nvidia / Ati drivers.  It will automatically detect the appropriate drive then install.
Reboot, then go run Nvidia X server settings to configure your twinview.
In the left hand pane select "X Server Display Configuration" 
Then on the right side configure twinview with the gui.   (Back up your X configuration file) Once your x config file is backed up then click "Save to X Configuration File" and restart the machine.  
This worked for me, but like i said....backup your x configuration file in case this doesn't work you can restore it.

---

### Post by Iwneferi on 2008-09-13
I think I might have it working! I'll post tomorrow when I've had a chance to try everything out. 

~Thanks!!!!!!!!!

---

### Post by michaelkahl on 2008-09-13
Fingers crossed, I hope so too.  Good luck and we look forward to hearing back.

---

### Post by Iwneferi on 2008-09-14
Yay! Everything's working just GREAT!!!

Thanks a ton!

---

