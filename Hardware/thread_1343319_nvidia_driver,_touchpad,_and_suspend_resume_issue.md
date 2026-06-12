---
title: "nvidia driver, touchpad, and suspend resume issue"
date: 2009-12-01
forum: Hardware
---

### Post by calbaker on 2009-12-01
My problem: 
Without installing any proprietary graphics drivers, I cannot resume from suspend or hibernate, but when I install NVIDIA accelerated graphics driver (version 185), my CPU fan never shuts off.  It's quite loud!  

To remedy this, I uninstalled this driver and installed version 173.  With version 173, the laptop fan operates properly, but on resume from suspend/hibernate, I lose my touchpad settings.  

I would like to have the full functionality of my graphics card, be able to hibernate/suspend with resume capabilities, and never have to mess with my touchpad settings.  

I recently did a fresh install of Ubuntu 9.10 Karmic Koala on my Dell Latitude D630 with 1.8 GHz core 2 Duo and 2 Gb of ram.  I set aside 4 Gb of ram to be used as swap.  I used the ext4 file system for the root partition.  I am dual booting with WinXP.  

As an aside, I am only keeping WinXP because I cannot do without Word and Excel.  My eventual plan is to use LaTeX and Matlab for everything I'd do in Word and Excel.  I also think LyX is pretty cool.

---

### Post by realzippy on 2009-12-01
Try the 190.42 driver.They fixed a lot...

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by calbaker on 2009-12-02
> **realzippy said:**
> Try the 190.42 driver.They fixed a lot...

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Interesting.  I want to try this, but I cannot get the *.run file to install correctly.  I tried simply clicking the file, and it opened with gedit.  After about a minute or so of watching a progress bar, I got the following error:

Could not open the file /media/Storage/Personal …ux-x86_64-190.42-pkg2.run using the Western (ISO-8859-15) character coding.

I also tried using the Current Locale (UTF-8) coding, and that yielded a similar result.  

Any advice?

---

### Post by realzippy on 2009-12-02
First uninstall the current nvidiadriver,Reboot.Do not log in (or log out),press Alt+ctrl+F2,log in at shell.Stop gnome by typing:
**sudo service gdm stop**
then navigate to the NVIDIAdriver (cd /media/Storage/Personal &#8230;),type:
**sudo sh NVIDIA** (hit Tab to autocomplete)
"yes" to asked question during install 
**sudo reboot**

---

### Post by calbaker on 2009-12-02
Installed.  I still have the same touchpad problem.  Whenever I resume from suspend or hibernate, all the touchpad settings are lost.  

If I could change the default touchpad settings, I think this would fix my problem.  

Also, the CPU fan makes a lot more noise with this driver.  Is there a way to change the temperature threshold?

---

### Post by AlexZaim on 2009-12-02
i have a question to the author of this thread (and, of course, anyone esle how can answer):

Does the driver enables you suspend, or did this feature worked out of the box? I installed this same driver but suspend still doesn't work. It shut's down completely. 

Thank you.

---

### Post by calbaker on 2009-12-02
> **AlexZaim said:**
> i have a question to the author of this thread (and, of course, anyone esle how can answer):

Does the driver enables you suspend, or did this feature worked out of the box? I installed this same driver but suspend still doesn't work. It shut's down completely. 

Thank you.

Suspend/hibernate did not resume until I installed an NVIDIA driver, and it immediately worked as soon as installed any of the proprietary drivers.

---

### Post by calbaker on 2009-12-04
Does anyone know how to preserve touchpad settings when resuming from suspend/hibernate?  Every time I resume, I have to fix the touchpad settings.  

That's my biggest problem with Ubuntu, and it's such a small issue!  I should be able to fix it somehow.

---

### Post by oooh on 2009-12-06
Hi there !

VAIO with NVIDIA here. Touchpad not working at all.

I think it is somehow related to NVIDIA drivers, but in my case, to ANY version of them, since 170 I believe.

Tuning XORG did not work. And now in 9.10 Koala xorg says that HAL is used from now on to manage I/O devices. 

I do not really know why it fails , but maybe related to your problem as well...

---

### Post by oooh on 2009-12-06
OK, more info here about the touchpad:

Finally I managed to make it run, without touching the NVIDIA drivers.

I just uncommented the xorg lines that ubuntu commented for me, and added a SHMConfig ON, after restart everything worked fine, even scrolling, tapping, and disabling the touchpad while writting!

Section "InputDevice"
# generated from default
Identifier "Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Protocol" "auto-dev"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "on"
EndSection

---

