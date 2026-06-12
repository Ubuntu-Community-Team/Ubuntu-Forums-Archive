---
title: "Hardware Drivers (jockey) shows no drivers in use."
date: 2010-02-24
forum: Hardware
---

### Post by kopatops on 2010-02-24
Hi!

I have played around with my NVIDIA video drivers for a long time. I'll post the entire procedure leading up to this point and my current problem after these steps in the end of the post. 

1. 'Hardware Drivers' (jockey app) shows an entry of 'NVIDIA driver - this driver is installed but not currently in use. 

2. I remove the driver and install the latest NVIDIA driver with their .run package.

3. I reboot; Ubuntu is run in "low graphics mode". 'Hardware Drivers' now shows no available NVIDIA driver at all. (But one modem driver entry.)

4. I put the keyword 'nvidia' into synaptic and boldly remove all installed packages listed.

5. I reboot; I get a desktop of a purple blob and some stains of white. Rubbish.

6. I switch to virtual console 3 and attempt to reinstall the downloaded drivers from same .run package.

7. The install script says it can't find the kernel source. I feel really stupid.

8. I reboot and choose an earlier kernel. Works in low graphics mode.

9. I uninstall/reinstall jockey ('Hardware Drivers') together with modaliases package and the NVIDIA .run package. Now things seem fine.

10. Hardware drivers now shows 3 options for NVIDIA drivers. They can either not be installed, or don't work at next reboot. So I recreate the configuration used after 9.

________________________________

So this is where I am now:

Jockey application is useless for installing any NVIDIA drivers and is unaware of the drivers actually installed and in use. Also tried the EnvyNG app, but it didn't work: 


```
mo@stupijar:/$ envyng -g
/home/mo/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
Traceback (most recent call last):
  File "/usr/share/envyng-qt/envyngqt.py", line 886, in <module>
    form = EnvyMainDlg()
  File "/usr/share/envyng-qt/envyngqt.py", line 290, in __init__
    self.abstract = abstraction.Abstraction(widget=self.pbar, text=None)
  File "/usr/lib/python2.6/dist-packages/Envy/abstraction.py", line 35, in __init__
    self.hardware = detection.HardwareDetection()
  File "/usr/lib/python2.6/dist-packages/Envy/detection.py", line 48, in __init__
    self.getCards()
  File "/usr/lib/python2.6/dist-packages/Envy/detection.py", line 141, in getCards
    self.nvidiaOrderedList = self.drivers['nvidia'].keys()
KeyError: 'nvidia'
```The problem is, in some situations (compositing and 3D games), the system is "not aware" of the graphics capabilities and the driver seems generally unstable and performs poorly.

I feel I have torn things apart here, and would like to make a clean NVIDIA drivers install. I don't expect anyone to help me patch up this leaking ship, I've been too reckless with it :). 

Is there any way to remove all traces of and references to NVIDIA drivers and then install a new driver? I would specifically like the NVIDIA 173 driver.

Tnx!
/kopatops

EDIT: I run a pre-release of Ubuntu!

---

### Post by kopatops on 2010-02-24
Update:

Hardware Drivers now shows that I have NVIDIA driver 173 installed, but not currently in use.

Back at the beginning ](*,) LOL

This makes my problem equivalent to the one described here:
[http://ubuntuforums.org/showthread.php?t=1386207](http://ubuntuforums.org/showthread.php?t=1386207)

Close thread?

---

### Post by Delan Azabani on 2010-02-28
I'm using Lucid as well and I'm having more and more problems with the nvidia drivers. I'd like to refer you to a [bug I have reported]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/525155") that details my problems. Not only does OpenGL act as if rendered by CPU (read: **slow**), when installed by Jockey it reports as "not in use".

Here's a way to clean up ***everything*** and use a non-accelerated driver (while running at the same high resolution you've come to love). I'd love to do GUI, but CLI is easier to explain:

sudo nvidia-uninstall
sudo apt-get purge nvidia-*
sudo rm /etc/X11/xorg.c*

The first one is just for .run drivers, while the second is for Jockey drivers. The third command removes ALL xorg.conf files - this is OK; the X server can run just fine without an xorg.conf file. Note how I didn't just remove the main one, I removed the xorg.conf.failsafe as well with a wildcard - **if you keep the xorg.conf.failsafe, Ubuntu will boot into a low-res mode**.

Hope that helped. So far, there's been no word on a fix for the bug, so I'm just running with no driver at all (at 1680x1050 still, of course) and that means no Compiz for me.

---

### Post by Delan Azabani on 2010-02-28
One more thing, please note that if you've had a .run package before, nvidia-uninstall won't clean up the .so files properly; whenever ldconfig is triggered you'll get a whole bunch of notices about empty symlinks to files. It is safe to remove the listed files (I have) if you aren't using the driver.

---

### Post by kopatops on 2010-03-05
Hi!
 
Thanks for the reply! 
 
This is exactly what I've been looking for. Did a search for NVIDIA and found all these junk .so files. Didn't figure out a way to remove them... 
 
So, anyway, I think jockey is a bit buggy and the drivers not showing up in that list doesn't necessarily mean a particular driver is not, de facto, in use. I wouldn't be able to use Compiz at all if it werent, right? It's just that the performance really *sucks* compared to the karmic release. Laggy window drag and such.
 
I'll try your wipeout method :) :) When I get home. Tired of workarounds. Because I honestly don't know what I'm doing half the time anyway when it comes to hardware drivers.
 
Thanks again!
/kopatops

---

### Post by finndo on 2011-10-21
I know this is an old thread, but I wanted to comment that this issue still happens in 11.10 Oneiric, I am having this issue with Jockey And AMD radeon drivers.  Here I was considering selling my brand new radeon and getting an Nvidia card to avoid all the hassles and I find that the common denominator, Jockey, is the most likely cause...

---

