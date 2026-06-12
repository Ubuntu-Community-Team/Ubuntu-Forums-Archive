---
title: "X won't load on AMD 64..."
date: 2004-12-31
forum: General Help
---

### Post by oberon on 2004-12-31
In trying to test out the 64-bit broadcom ndis drivers I loaded the 64-bit version of Ubunuu back on my pc and was soon reminded of the other reason I put the i386 version.  I can't start X.  It seems to be replated to module v4l.  XF86 log shows that  it fails to load beacuse it could not be found.  I tried to comment it out but it still crashes the X server.  I am running on Warty (64-bit), XFree86, nVidia geforce 4 440 GO.  Any ideas? Please...

-oberon

See [http://www.ubuntuforums.org/showthread.php?t=9593](http://www.ubuntuforums.org/showthread.php?t=9593) for info on the 64-bit NDIS driver for broadcom.

---

### Post by oberon on 2004-12-31
After looking into it with a few cups of cofffe in me I noticed that it doesn't look like the v4l  (video 4 linux) module is even there.  I checked /usr/X11R6/lib/modules/drivers and well its not there.  Is it somewhere else?  How do I get it installed.  I tried doing a fresh install of Ubuntu again nothing, reinstalled gdm after install nvidia-glx, nothing.  I get the nvidia splash and then back to cli with an error "Fatal server error; Caught Signal 11."  Any ideas?

-oberon

---

### Post by linuxgrrl on 2005-01-01
I am having the exact same problem, also on a 64 bit system.  The most frustrating is that it DID work fine for about an hour ... right after I did "apt-get install nvidia glx" and "nvidia-glx-config enable" then ctrl+alt+backspace, I had TV-out, NVIDIA splash screen, everything perfect.

Then I rebooted, and gdm will not start.   The message says "skipping /usr/X11R6/lib/modules/fonts/libspeedo.a:spencode.o" right before it fails with "no available display."  Any ideas welcome ... I really don't want to go back to Mandrake :)

---

### Post by linuxgrrl on 2005-01-01
OK, after an hour of fun I have this working.   It seems that the NVIDIA drivers are not happy unless they are compiled specifically on your machine.  Luckily this is not difficult:

1. step one I installed the kernel headers for my system:

uname -r      #this provides kernel version
apt-cache search <kernel version>     # this will report back the available packages

apt-get install <kernel headers package>

2. step 2 I installed the NVIDIA drivers using the NVIDIA-provided .run file, available here:  
[http://www.nvidia.com/object/linux_display_amd64_1.0-6111.html](http://www.nvidia.com/object/linux_display_amd64_1.0-6111.html)

[Note, there is a newer version available but some have reported problems with it ...]
I got a lot of error messages during this step with various parts of /usr/X11R6/ not found, but I just ignored them and continued.

3.  edited the XFree86 config file as directed by the NVIDIA installer; and
4.  ran "gdm" and everything's OK now.   Weird.

UPDATE: eventually, the time came when I had to reboot and unfortunately x did not start properly.  This time, the solution was to load nvidia module manually from the commandline with "insmod nvidia", then run "gdm."  *sigh*

---

### Post by oberon on 2005-01-02
I ended up re-loading with a hoary snapshot and video atleast works with the nv driver now.  The nvidia 6629 driver still doesn't work.  I may try the one directly from nvidia (as you suggested) and try again.  Thanks.

---

### Post by oberon on 2005-01-05
Okay I tried the 6111 driver and had no luck with it so I went back to 6629.  I found that EDID does not detect the correct settings which is what crahes X.  If I use the ["IgnoreEDID" "1"] setting in xorg.conf I get a horribly distored split screen.  After read through the README I found something in Apendix K that talks about configuring the nvidia module with differant EDID settings.  So after playing with that I found that doing the following allows X to run.
```
sudo modprobe nvidia NVreg_SoftEDIDs="0" NVreg_Mobile="0"
```
But, how do I make this permenant?  I have to do this every time the pc boots.  I tried placing the options in the "Modules.conf" file as recomended in the README file, but is has not effect.

---

