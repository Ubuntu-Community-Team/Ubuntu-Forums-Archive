---
title: "Low resolution login??"
date: 2008-07-28
forum: Hardware
---

### Post by ravl on 2008-07-28
I have Kubuntu 8.04.1 for amd64 on a HP Pavillion dv6810. I installed the Nvidia drivers using envy-ng, and they work correctly once logged in to KDE. But the KDM login page is always in low resolution (640x480). The moment I log in, everything jumps to high resolution just as my mouse cursor theme is applied.

Could the drivers be just installed for the user, and not globally? I have gone through kdmrc and there are no options there relating to resolution.

Attached is my xorg.conf, maybe that can help fix this.

---

### Post by SZorg on 2008-07-28
Are you using two monitors? "Screen1" shows a resolution capability of ONLY 640x480@60hz. If you are not using two monitors you may try backing up your xorg.conf, removing (or commenting out) that section and trying again. You may also try changing that 640x480@60 to 1280x800@60 or whatever you normally use and then rebooting or restarting X.

---

### Post by ravl on 2008-07-28
I just tried that, both commenting out and deleting the sections that had a 640x480 resolution. Also, I changed them to a higher resolution and nothing worked.
What I did was:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to return to the default configuration. I chose my monitor model in System Settings, and restarted.
Now everything was in low-res, both KDM and KDE. Then I edited the xorg.conf and replaced the two occurrences of 'vesa' by 'nvidia' and restarted X again.
This reproduced the original behavior, having KDM in low-res and KDE in high-res, so I think it's a driver issue rather than a misconfiguration.

---

### Post by irlandes on 2008-07-29
I am encountering the same problem in a  W3115 emachines desktop, using 32 bit Kubuntu on the 64 bit machine.  xorg.conf is really screwy on mine.  Nothing like xorg.conf on Freespire 2.0.8, which is Kubuntu 7.04 based.  And, nothing like yours, either.  I will be watching this posting and will be passing on anything I learn.  I have worked with xorg.conf for some years, this is really different.

I copied in xorg.conf from Freespire on the same machine, multiboot, and resolution was okay, but the mouse is dead.

---

### Post by irlandes on 2008-07-29
[http://kubuntuway.net/forum/showthread.php?p=262](http://kubuntuway.net/forum/showthread.php?p=262)

This linked thread gives us a major clue to this problem. Dexconf and debconf.  I will let you read it for yourself because I don't yet understand it.

---

### Post by irlandes on 2008-07-29
There is a new utility to set resolution. xrandr

Type:

 xrandr <enter> 

on a terminal, and it is supposed to tell you the possible resolutions available.

Then, to change you type:

xrandr -s 1024X768 <enter>

[http://www.linuxtutorialblog.com/post/solution-resetting-your-screen-resolution-with-xrandr](http://www.linuxtutorialblog.com/post/solution-resetting-your-screen-resolution-with-xrandr)

Someone has said to set refresh rate at the same time:

xrandr -s 1024X768@75

if you want the refresh rate to be 75 Hz.

Will keep you posted.

---

### Post by irlandes on 2008-07-29
On mine, command xrandr shows only 4 very poor resolutions. I dug into /var/log/Xorg.0.log (using:  sudo nano /var/log/Xorg.0.log <enter> and discovered the log showed problems reading the monitor DDC (apparently how a computer does plug and play) though Freespire does it okay.

It also showed sync range of 31.50-37.90 kHz  and vrefresh range of 50.00-70.00 Hz.    Another user showed his Xorg.conf for the same monitor as:

HorizSync 30.0 - 70.0
VertRefresh 50.0 - 160.0

The log file then showed a large number of resolutions  not usable because the hsync or vrefresh was out of range, meaning the wrong range the machine selected because it can't read the DDC correctly.

I checked an old Mandriva 2007 xorg.conf and it had the same wide rates shown above.

So, the problem FOR ME is failure to read the DDC when other distros will read it fine.

---

### Post by irlandes on 2008-07-30
Solved. It was the nvidia drivers on my machine.

I found and now can't find it again, a posting somewhere which said to go to   SYSTEM ==> HARDWARE DRIVERS MANAGER and enable the nvidia driver. When I did, it kicked on the download system, downloaded and installed the latest nvidia driver, 169.12, but perhaps a patched version, I don't know how to get the other numbers.  When I rebooted, it worked perfectly.

And, the problems all went away.  EDID reads the DDC; it has all the options.

I can't say if it will work for you or not.

---

### Post by ravl on 2008-07-30
I tried your suggestion of using the hardware drivers manager, and it didn't work. The X server failed to start, so I used envyng again to install the envy drivers. That got me to my original behaviour, KDE works well, on high-resolution and widescreen settings. But KDM remains in 640x480 and not in widescreen mode.

Thanks for the info, irlandes

---

### Post by irlandes on 2008-07-30
The only two suggestions I could possibly make:

1.  sudo nano /var/log/Xorg.0.log and read carefully through it to see if there is an explanation as to reasons for not enabling anything else. In my case, in each possible resolution it stated either the frequency of h or v was out of spec, thus could not run.

There was also a reference to reading the monitor i.d. information; ddc1 failed but ddc2 passed.

2.  One could go directly to Nvidia and download a newer or older version; some have said the older versions work.  I found it with nvidia download for Google.   One runs a certain command ending with .sh, I think.  Then reboot or restart and see what happens.

You should be able to do this from a terminal prompt if X completely breaks, well, maybe not the download, but the install.  And, with any resolution, should be able to get the download, yes?  Of course, I learned how to fix things from the prompt back in Mandriva 9.? days since that is what one had to do so it may be easier to say than to do.

Of course, I assume you have used   xrandr   at the command line to see what it is enabled to run.  You might post that here, though it is pretty obvious.

Last resort, try to switch to vesa or ati depending upon your video card, which I am guessing is Nvidia.

---

### Post by ravl on 2008-07-30
Here's a part of /var/log/Xorg.0.log, that seems to report the switching to low-resolution. I couldn't find anything that points to X switching back to high-resolution inside KDE, though.

```
II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7150M / nForce 630M (C67) at PCI:0:18:0
(II) NVIDIA(0):     (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.67.32.16.17
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7150M / nForce 630M at
(--) NVIDIA(0):     PCI:0:18:0:
(--) NVIDIA(0):     AUO (DFP-0)
(--) NVIDIA(0): AUO (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): AUO (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1280x768@60"; removing.
(WW) NVIDIA(0): No valid modes for "800x600@56"; removing.
(WW) NVIDIA(0): No valid modes for "1280x720@60"; removing.
(WW) NVIDIA(0): No valid modes for "1280x800@60"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "800x600@60"
(**) NVIDIA(0): Virtual screen size configured to be 1280 x 800
(--) NVIDIA(0): DPI set to (61, 72); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
```

---

### Post by irlandes on 2008-07-30
Here is where my Dell laptop with 6 series video card loads the module, so you can see it is version 169.12


> (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX

Next is where it sets the resolution.  The monitor is an eview 17f3.

> (II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6100 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6100 at PCI:0:5:0:
(--) NVIDIA(0):     EMA eView 17f3 (CRT-0)
(--) NVIDIA(0): EMA eView 17f3 (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (81, 81); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp

Here is what I had with the  bad version:

> (II) NV(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) NV(0): Unable to estimate virtual size
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (hsync out of range)
(II) NV(0): Not using default mode "1280x768" (hsync out of range)
(II) NV(0): Not using default mode "640x384" (hsync out of range)
(II) NV(0): Not using default mode "1280x800" (hsync out of range)
(II) NV(0): Not using default mode "640x400" (hsync out of range)
(II) NV(0): Not using default mode "1152x768" (hsync out of range)
(II) NV(0): Not using default mode "576x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(--) NV(0): Virtual size is 800x600 (pitch 800)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 $
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 $
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -$
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 d$
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 d$
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 d$
(==) NV(0): DPI set to (96, 96)

Here is command xrandr now that it is working:

> @W3115:~$ xrandr
Screen 0: minimum 320 x 175, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    51.0     52.0     53.0     54.0
   840x525        55.0
   832x624        56.0
   800x600        57.0     58.0     59.0     60.0     61.0     62.0     63.0
   800x512        64.0
   720x450        65.0
   720x400        66.0
   640x512        67.0
   640x480        68.0     69.0     70.0     71.0     72.0
   640x400        73.0     74.0
   640x384        75.0
   640x350        76.0
   576x432        77.0
   576x384        78.0
   512x384        79.0     80.0     81.0     82.0     83.0
   416x312        84.0
   400x300        85.0     86.0     87.0     88.0     89.0
   360x200        90.0
   320x240        91.0     92.0     93.0     94.0
   320x200        95.0
   320x175        96.0


For latest version with manual install (you can do this in command mode if X crashes) :

[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

This next one the well known R. Profitt discusses what to do if there are problems with older versions:

[http://forums.cnet.com/5208-7813_102-0.html?forumID=26&threadID=251500&messageID=2509897]("http://forums.cnet.com/5208-7813_102-0.html?forumID=26&threadID=251500&messageID=2509897")

Here is a page which links you to the archives for older versions.  Profitt says the package checks your card before installing:

[http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")

---

### Post by rmdegennaro on 2009-03-02
I've had a similar issue with one desktop and now with my virtual machines (since upgrading to VMWare Fusion 2.0.2).  

Basically, these machines always default to 640x480 or 800x600 resolution, though they can do much higher resolution.  This also messes with the panels and widgets in both GNOME and KDE (alignments seem to be set at GD/KDM and not when logging in).  

This help page shows how I solved the issue, though the resolution is now "hard coded" or permanent:  [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

One misleading thing is the line to set resolution.  The command that worked for me is "xrandr -s 1280x960", though one could use another resolution is needed and appropriate for the videocard/monitor.  

I hope this helps someone and saves them a few hours of searching around like I just did.  :-)

---

### Post by rmdegennaro on 2009-03-02
Oh, and when I get a bit more time, I will search the bug database(s) for why KDE doesn't set resolution apon login (only after going to System Settings -> Display).

---

