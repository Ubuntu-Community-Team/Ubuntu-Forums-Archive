---
title: "Sony Screen Resolutions"
date: 2013-04-21
forum: Hardware
---

### Post by motobeats on 2013-04-21
I am using an Intel [NUC]("http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/next-unit-computing-introduction.html") to connect to my Sony Bravia 48" TV as a home theater system. I am using 12.04.

My problem is that from the couch, the text on the screen is too small so I wanted to reduce the resolution in Display. I found a setting that worked (one of the 16:9 options) but then I ran all of the updates for 12.04. On the next restart, I got an error with respect to a long list of resolutions options that failed.

Now, instead of a long list of resolution options in Display, I have 5 and only 2 are 16:9. And when I switch to the lower resolution, the edges of the screen are cut off.

Any help on restoring more Display resolution options (like before the update) or fixing the cut off edges (already checked for scan options in my TV's menu and could find any) would be much appreciated.

Thank you.

---

### Post by motobeats on 2013-04-22
I tried to move my Ubuntu 12.04 on my Intel NUC to my Samsung TV and I have the same issue. The edges of the screen are cut off.

The Samsung in a 48" connected with HDMI. Shows up in Ubuntu as Samsung Electronic Company 7".

For resolutions I only have 2 options with 16:9 ratio. Both cut off the edges. For the Samsung, I found not options in the TV's menu that fixed this issue. No options that refer to scan or progressive scan.

---

### Post by papibe on 2013-04-22
Hi motobeats.

That sounds like [Overscan]("http://en.wikipedia.org/wiki/Overscan"). In other words, a problem in the HDTV settings.

If so, you have 2 options to solve it:

First (recommended): Some TV's have the ability to set how the signal is reproduced. In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Play with the options available on your TV, may be the option is not easy to see. Check your manual or research about it on the Internet.

Let us know how it goes,
Regards.

---

### Post by motobeats on 2013-04-23
Thanks for the reply. 

Back to the Sony Bravia since at least it gets me close:

Sony 72": Resolution setting in Ubuntu: 1920x1080 (16:9) 
     -  This fits the screen on the TV's "Full Pixel" setting. But it is too  small to see from the couch. For other TV settings, I lose the edges (as  expected)

Sony 72": Resolution setting in Ubuntu: 1280x720 (16:9)
     - This is the only other 16:9 resolution setting available to me in  Ubuntu (I had more prior to Ubuntu updates). 
     - In "Full Pixel" I get the  whole desktop but my TV shrinks the image down the the middle portion of  the screen (3" of black pixels all the way around my desktop). 
     - "Full"  gets me closets to using the full screen but I lose the edges. I did  find some TV settings to shrink the image by a few lines but it isn't  enough to give me the ends of the desktop.

Prior to updating  12.04, I had a few other 16:9 resolution options. How do I get those  back? Other solutions are welcome as well.

---

### Post by papibe on 2013-04-24
Glad you are making progress.

Unfortunately, neither of the Ubuntu flavours are very usable on a [10-foot user interface]("http://en.wikipedia.org/wiki/10-foot_user_interface"). I'd love to see something like a special interface, or just a good theme to work better from the couch.

I had relative good success on the browser using the Firefox's plugin called [NoSquint]("https://addons.mozilla.org/en-us/firefox/addon/nosquint/"), although it does not change the tab's size.

If the main purpose of the machine is to be HTPC, I would recommend 'living' more inside XBMC. It's interface is is perfect to operate from the couch, and it has several useful plugins, like youtube, hulu, etc.

If your assessment is that the best solution is using the lost resolutions, I can think of a few of solutions:

Use xrandr (command line) to inspect hidden resolutions and force a new resolution.

Forcing driver version:
[LIST]
[*]First using synaptic, uninstall the current intel driver, and then install the previous one.
[*]Then you can force that version so it won't be upgraded.
[/LIST]
Get modeline from previous driver:
[LIST]
[*]First using synaptic, uninstall the current intel driver, and then install the previous one.
[*]Then use xrandr and/or xvidtune to get the modelines from the desired resolutions.
[*]Then upgrade to the current driver and force those modelines (resolution) on the new driver using xrandr.
[/LIST]
Let us know if you need more help with that.
Regards.

---

### Post by motobeats on 2013-06-27
Finally getting back to this now. I uninstalled anything I could find with an "intel" search in Synaptic related to graphics and after restarting I still did not have all of the original resolutions options in Display.

As for installing the old display driver, I'm not sure how to find what my current one is let alone what it was before the upgrade.

Any help would be much appreciated. I'm in over my head on this one.

---

### Post by motobeats on 2013-07-01
Here is the update on this saga:

1. Tried NoSquint. Pretty happy with the results so Firefox is now visible. However I am still squinting outside of Firefox. And to be honest, I want to figure out how to get the old resolution settings back (after all, I wouldn't have installed Ubuntu if I didn't want to tinker).
2. Removed "intel"  driver intel_drv.so by removing the package via Synaptics. This did not change the resolution options available in Display. Reinstalled (via Synaptics) what I believe to be the old module which did not work either. Here is a snippet from the Xorg.log (which I really don't understand). Not sure which drivers control the options available in Display.

```
[     3.825] (II) LoadModule: "intel"
[     3.825] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     3.827] (II) Module intel: vendor="X.Org Foundation"
[     3.827]    compiled for 1.13.0, module version = 2.20.9
[     3.827]    Module class: X.Org Video Driver
[     3.827]    ABI class: X.Org Video Driver, version 13.0
[     3.827] (II) LoadModule: "vesa"
[     3.827] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     3.827] (II) Module vesa: vendor="X.Org Foundation"
[     3.827]    compiled for 1.13.0, module version = 2.3.2
[     3.827]    Module class: X.Org Video Driver
[     3.827]    ABI class: X.Org Video Driver, version 13.0
[     3.827] (II) LoadModule: "modesetting"
[     3.828] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     3.828] (II) Module modesetting: vendor="X.Org Foundation"
[     3.828]    compiled for 1.13.0, module version = 0.5.0
[     3.828]    Module class: X.Org Video Driver
[     3.828]    ABI class: X.Org Video Driver, version 13.0
[     3.828] (II) LoadModule: "fbdev"
[     3.828] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     3.828] (II) Module fbdev: vendor="X.Org Foundation"
[     3.828]    compiled for 1.13.0, module version = 0.4.3
[     3.828]    Module class: X.Org Video Driver
[     3.828]    ABI class: X.Org Video Driver, version 13.0

```

3. Booted the original iso from USB (which has a lot more resolution choices in Display). Selected the resolution I wanted and used xrandr --verbose to get the right modlines

```
1360x768 (0x53)   85.5MHz +HSync +VSync *current
        h: width  1360 start 1424 end 1536 total 1792 skew    0 clock   47.7KHz
        v: height  768 start  771 end  777 total  795           clock   60.0Hz

```

4. My next step is to add the modlines above but I want to do it permenantly. I found this [procedure]("https://wiki.archlinux.org/index.php/Xrandr") (haven't tried it yet).
4a. For the current version of X xorg.conf does not exist by default. And it is a bit tricky to create it since X can't be running. Fortunately I came across rainboxagent7's comment on this [thread]("http://ubuntuforums.org/showthread.php?t=1437980")

So I am still working through step 4 with the hope at the end that I will have the resolution in Display I want (and it will survive reboots)

Any advice is welcome. Especially explaining where my resolution options went in the first place and what I am doing wrong in trying to roll back updates to restore them.

---

### Post by motobeats on 2013-07-03
Tested desired resolution addition via xrandr at the tty and got this error.


andrew@Ubuntu-TV:~$ sudo xrandr --addmode HDMI1 1370x768_60.00 xrandr: cannot find mode "1370x768_60.00"
I think I'm pretty stuck at this point. Cannot find a fix that didn't involve a typo by the user.

Considering rolling back to a fresh install and just not doing any updates.

---

### Post by motobeats on 2013-07-04
Found the problem. Here is my latest install from apt/history.log

Start-Date: 2013-07-04  09:10:11
Commandline: aptdaemon role='role-commit-packages' sender=':1.48'
Install: linux-image-3.5.0-34-generic:amd64 (3.5.0-34.55~precise1)
End-Date: 2013-07-04  09:10:43


And the error I got after rebooting. Planning to roll back this latest update to try and get my resolutions back.
Thoughts on what the issue is?

```
Could not apply the stored configuration for monitors

none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 63
CRTC 63: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
Trying modes for CRTC 65
CRTC 65: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
```

---

### Post by motobeats on 2013-07-04
Rolled back offending kernel update and my resolutions are back. Don't know what the issue is though. Just going to skip that update in the future.

---

