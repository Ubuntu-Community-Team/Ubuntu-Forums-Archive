---
title: "nvidia driver troubles"
date: 2008-10-25
forum: General Help
---

### Post by bbyam on 2008-10-25
Hello, I am new to Ubuntu and Linux, but fairly familiar with general stuff and the terminal.

It all started with a problem where full screen programs would always randomly get kicked out of full screen and into windowed mode. So the first thing I decided to try was updating the nvidia driver.  I got the latest one from nvidia.com, version 177.80, stopped X, and ran the installer (NVIDIAxxxxx.run).  When it was done, my screen mode was limited to 800x600, and I can't get it any higher.

I have tried numerous things to fix this, including installing version 173.14.12 from nvidia.com, uninstalling that with "sh NVIDIAxxxx.run --uninstall" and trying to completely remove, reboot, and re-install the nvidia-glx-new from the repository.  I've also gone through all the instructions from these 2 links:
[http://ubuntuforums.org/showthread.php?t=481887](http://ubuntuforums.org/showthread.php?t=481887)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
with no luck.

xorg.conf always shows "Unknown" for the monitor after reconfiguration and lists no modes (adding modes doesn't help, either).

I also kept trying to run nvidia-settings and every time, no matter what state my system was in, it kept saying it appeared that I wasn't using an nvidia driver and wouldn't come up. My guess is that the driver just isn't working right and X can't ever detect the monitor.

When I boot, after the Ubuntu screen, it shows some terminal stuff, and the screen blanks out a few times before giving me a 'low resolution' warning.

I'm using Ubuntu 8.04 and nVidia 7150 video card.

Any help would be greatly appreciated! Thanks.

---

### Post by eternalnewbee on 2008-10-25
What message do you get in Main Menu > System > Administration > Hardware Drivers?

---

### Post by bbyam on 2008-10-25
First, I would see driver there the same as when it was running correctly, but the checkbox would be unchecked.  I would check it, and would tell me I need to restart.  Every time I'd restart, it would be unchecked again.

Later it was checked, but nvidia-settings still would not run saying I didn't have a driver loaded.

At this point right now, the box is blank and it says "No proprietary drivers are in use on the system."

The last thing I did was a complete removal of nvidia-glx-new, reboot, then re-install of nvidia-glx-new, then reboot again.

---

### Post by bbyam on 2008-10-26
Okay, I figured it out.

I read a thread regarding a previous version of ubuntu that talked about them installing the nvidia-glx-new package. They did, and it didn't work, and they found out the problem is because the nvidia-glx-new package relies upon the linux-restricted-modules package, but it didn't automatically install that, they had to install it themselves.

So one of the things I tried was completely removing that package, rebooting, then adding it back in.  My problem was that I added back in the linux-restricted-modules-2.6.24-21-**368** package when I should have added the linux-restricted-modules-2.6.24-21-**generic** package.  More so, the default column widths of Synaptic Package Manager don't show far enough to see which version was installed.  So I flew past it every time, even doing a re-install not knowing I was installing the wrong one.

So I removed the 386 version and put the generic back in, rebooted, and that made everything work again with the standard ubuntu included nvidia driver (version 169.something).

I didn't put the wrong version in until after everything was broken, so it seems the driver from nvidia's web page, 177.80, still won't work for me.

So I'll wait for ubuntu Intrepid to see if I still have my original full screen problem before investigating further.

---

