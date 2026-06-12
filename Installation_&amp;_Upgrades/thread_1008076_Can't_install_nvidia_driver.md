---
title: "Can't install nvidia driver"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by Madwand on 2008-12-11
I've been searching for several hours now and found no answer to this problem. I just upgraded from Ubuntu 8.04 to 8.10, and my monitor is stuck at 800x600 resolution, when it should be 1280x1024. An improved resolution is not available using the "Screen Resolution" tool. I think this may be because I'm not using an nvidia driver.

My GPU is a GeForce 4 MX integrated. I know that 3d acceleration isn't supported for this chip, but that's fine -- I just want 2d acceleration and the correct resolution for now!

I tried installing nvidia-glx using synaptic, but I get the message "Could not mark all packages for installation or upgrade", and "Package nvidia-glx has no available version, but exists in the database." So instead, I also have tried installing nvidia-glx-96, which is apparently the version that supports my GPU. This works, but going to System->Administration->Hardware Drivers doesn't show any options for switching to a new driver.

So, please help! What can I do to get some decent resolution for my monitor? I tried editing xorg.conf, but what I've tried so far hasn't worked -- and I didn't need to do much of anything to get my system to work in Ubuntu 8.04.

---

### Post by prshah on 2008-12-11
> **Madwand said:**
> 
my monitor is stuck at 800x600 resolution, when it should be 1280x1024. 

Short-circuiting everything else (assuming driver installed, etc etc) this should work; open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo xrandr --fb 1280x1024
```

Post back (with error messages, if any) if this doesn't work.

Note: There is a (small) element of risk that your monitor may not support a combination of refresh rate / resolution; so you do this at your own risk.

You may need to Auto-Adjust your screen (if LCD) after this command.

---

### Post by ellalan on 2008-12-11
> **Madwand said:**
> I've been searching for several hours now and found no answer to this problem. I just upgraded from Ubuntu 8.04 to 8.10, and my monitor is stuck at 800x600 resolution, when it should be 1280x1024. An improved resolution is not available using the "Screen Resolution" tool. I think this may be because I'm not using an nvidia driver.

My GPU is a GeForce 4 MX integrated. I know that 3d acceleration isn't supported for this chip, but that's fine -- I just want 2d acceleration and the correct resolution for now!

I tried installing nvidia-glx using synaptic, but I get the message "Could not mark all packages for installation or upgrade", and "Package nvidia-glx has no available version, but exists in the database." So instead, I also have tried installing nvidia-glx-96, which is apparently the version that supports my GPU. This works, but going to System->Administration->Hardware Drivers doesn't show any options for switching to a new driver.

So, please help! What can I do to get some decent resolution for my monitor? I tried editing xorg.conf, but what I've tried so far hasn't worked -- and I didn't need to do much of anything to get my system to work in Ubuntu 8.04.
In synaptics enable EnvyNG and use that to find and install the driver. This is the easiest method.

---

### Post by ellalan on 2008-12-11
You can also search for your driver at [www.nvidia.com](www.nvidia.com).
I found the driver is version 96.43 for your graphics.(you make sure you get the right one)
Download the driver to your Desktop.
1. Uninstall everything begins with "nvidia" in synaptics.
2.Ctrl+Alt+F1
3. sudo /etc/init.d/gdm stop
4.cd Desktop (note the D is capital)
5.sudo sh NVIDIA press Tab (the rest of the version number will be entered)
6.sudo reboot
Thats all you have to do to install a new driver. HTH.

---

### Post by Madwand on 2008-12-11
I used EnvyNG to install a driver successfully, but upon restart, there was no change to my resolution, and the Screen Resolution tool still shows no resolutions available above 800x600. System->Administration->Hardware Drivers still says "No proprietary drivers are in use on this system." When I run nvidia-settings, it tells me, "You do not appear to be running the nvidia X driver."

I used the "sudo xrandr" command, and got this error: "xrandr: screen cannot be larger than 800x600 (desired size 1280x1024)"

Will I have to download and install drivers directly from nvidia to get this to work? I am reluctant to bypass Synaptic unless I know that is what I have to do to get a better screen resolution.

---

### Post by Madwand on 2008-12-12
I still haven't figured out how to get a decent screen resolution. Any more ideas? Or will I have to reinstall Hardy Heron? I'd really prefer not to do that.

---

### Post by Bear Knuckle on 2008-12-12
> **Madwand said:**
> I still haven't figured out how to get a decent screen resolution. Any more ideas? Or will I have to reinstall Hardy Heron? I'd really prefer not to do that.

Have you tried to change in manually in the xorg.conf?

---

### Post by Madwand on 2008-12-12
I've tried a couple different changes to xorg.conf, but nothing I've done has worked so far. Notably, the changes discussed here:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

... didn't do anything, although I may have missed some crucial step.

---

### Post by Bear Knuckle on 2008-12-12
> **Madwand said:**
> I've tried a couple different changes to xorg.conf, but nothing I've done has worked so far. Notably, the changes discussed here:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

... didn't do anything, although I may have missed some crucial step.

Have you tried this:

```
Section "Monitor"
    Identifier      "External DVI"
    Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Option          "PreferredMode" "1280x1024_60.00"
EndSection

```
???

---

### Post by Madwand on 2008-12-12
I added the "Modeline" and "Option" lines to the already-existing "Monitor" section in my xorg.conf. I did not set the "External DVI" identifier, and kept that line as it already existed. This is because I don't have a DVI monitor, I just use an ordinary VGA cable. I don't know enough about what those lines actually mean to know if what I did was correct.

---

### Post by Bear Knuckle on 2008-12-12
> **Madwand said:**
> I added the "Modeline" and "Option" lines to the already-existing "Monitor" section in my xorg.conf. I did not set the "External DVI" identifier, and kept that line as it already existed. This is because I don't have a DVI monitor, I just use an ordinary VGA cable. I don't know enough about what those lines actually mean to know if what I did was correct.

Can you paste your "Modeline" line (...) in here?

**edit:** Forget the "Modeline" entry... what's in section "*Screen*", Subsection "*Display*" in the entry "*Modes*"?

It should look something like
```
Modes    "800x600" "640x480"

```

Try to add your desired resolution, like
```
Modes    **"1280x1024"** "800x600" "640x480"

```
for 1280x1024 pixels.

If those changes are needed, e.g. if the maximum resolution **before** your changes was "800x600", then you should be able to change the resolution to the desired value after a x-server restart.

---

### Post by Madwand on 2008-12-12
Any more ideas here folks? I still haven't solved this problem. A bit more information for you:

When booting up, I can see a line for installing nvidia driver 96.43... flash by. It also says "failed" in bright red letters. I assume this means I have no driver. I know that my GPU doesn't work well with the latest xorg, but is there anything at all I can do, any driver I can use, that will install correctly?

I've also played around with xrandr quite a bit, and I can ask it to use a higher resolution. I have to tell it to use the "default" output (VGA doesn't work, although I don't know what possible outputs exist). However, on the final "xrandr --output default --mode 1024x768" command, I get this error:

xrandr: Configure crtc 0 failed

I'm still looking for ideas. At this point it very much looks like I need a driver, any driver that works with my GPU and will actually install. What can I do?

---

### Post by Madwand on 2008-12-12
> **Bear Knuckle said:**
> 
If those changes are needed, e.g. if the maximum resolution **before** your changes was "800x600", then you should be able to change the resolution to the desired value after a x-server restart.

Yes, I have tried this. I'll go ahead and show my entire xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nv"
#        Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
#        Option          "PreferredMode" "1280x1024_60.00"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSectionection "Device"
	Identifier	"Configured Video Device"
	Driver	"nv"
#        Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
#        Option          "PreferredMode" "1280x1024_60.00"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

As you can see I'm using the "Modes" line. The 2 lines commented out are my attempt to set the display section. Unfortunately, X won't start if I do this and I had to comment those lines out in recovery mode.

I still think this has something to do with a driver problem. It's going by so fast I can barely read it (and it isn't logged anywhere I can find), but I'm getting a couple messages saying that something failed on boot, one of them being the Nvidia 96.43 driver. I need an alternate driver to try, as the one that comes from using EnvyNG doesn't work on my machine. Help, please!

---

### Post by Madwand on 2008-12-12
Alright, it seems apparent after 2 days of struggling with this problem that Intrepid is simply incapable of running on my hardware. This is extremely disappointing. I hope this issue is fixed in the next version of Ubuntu. For now I guess I'm forced to reinstall Hardy.

It would be very nice if this issue was documented. I was warned that 3d wasn't working for my GPU, but not that the driver wouldn't work at all!

---

### Post by Bear Knuckle on 2008-12-13
Sorry Madwand, I am having trouble here too. At the mom I can only run my pc with live cds, i am unable to install or backup the data on my disks. :-(

So i can't help you at the mom. I don't think, Intrepid is not able to run, you can fix this.

---

