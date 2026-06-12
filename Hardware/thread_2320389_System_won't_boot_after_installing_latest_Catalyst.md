---
title: "System won't boot after installing latest Catalyst driver"
date: 2016-04-13
forum: Hardware
---

### Post by Grundoko on 2016-04-13
I was originally running the Catalyst driver from the Ubuntu Additional Drivers application. Divinity: Original Sin was crashing periodically, and I thought it might have been the outdated driver, so I tried to install a newer version from AMD's website.

What I did:
I first used the Additional Drivers dialogue to "uninstall" the catalyst driver by switching back to the open source driver. Unfortunately, it seems the tool isn't very intelligent, because it didn't fully remove catalyst. 
When I tried to run the catalyst installer, it told me that there was a previous installation, and that I should remove it first. 
The recommended way to remove the catalyst driver is to run 'amdconfig --uninstall'. Unfortunately, I no longer had that commend because Additional Drivers had removed it.
Thinking that the only thing remaining from the old driver was the xorg.conf file, and that it would be overwritten when I installed the new driver anyway, I decided to run the installer with --force.

What happened:
Upon rebooting, I was greeted with a fullscreen terminal that shows
```

fsck from util-linux
recovering journal

```

I can't even access the fallback terminal. When I attempt to access the fallback terminal, it will show for just a moment, and then start flickering back and forth between the fallback terminal and this error message. After a few moments, the system becomes entirely unresponsive (stops flickering and stops accepting input).

I've tried booting with the nomodeset parameter. It doesn't change the issue. The fullscreen terminal just runs at a lower resolution, and therefore has larger text. No other differences.

Any help would be greatly appreciated. I've been running Ubuntu since 7.10, and have had a multitude of issues with graphics drivers in the past. Not once however, have I had a graphics driver break my system to the point where I could not access the fallback terminal.

---

### Post by T.J. on 2016-04-13
I play Divinity:OS on Linux myself, and I sympathise. =(

I'm very sorry to say that you should ***never, ever*** use the Catalyst driver provided on the AMD website without very careful consideration. The driver on the AMD website is not intended for normal users, because it breaks packaging.  The AMD installer breaks the OpenGL Mesa libraries (on purpose) that are used by Ubuntu. Normally, the package manager repairs it seamlessly, but if you install/uninstall the Catalyst driver manually by yourself, it can't.

Once that happens, the X11 windowing system can't function properly, and will become unstable - if it works at all. What might make your day harder us that newer versions of Ubuntu try to start X11, even when using recovery mode.  If you do get a black screen or flashing, try control+alt+ F1 (after the machine is booted as far as it can) to get to the terminal prompt.  It might work, or it may not, depending on the severity of the problem.


 If that is not possible, you will need to use a boot disc (or usb) and then mount the drives manually.  I can show you how, but please test the recovery option first.  It's a lot simpler.




Once logged in, you need to repair OpenGL:

1. Make sure that all files that start with "xorg.conf" in /etc/X11 are deleted.

sudo rm /etc/X11/xorg.conf* -rf

2.  Execute two commands to repair Mesa:

sudo apt-get install --reinstall libgl1-mesa-glx
sudo apt-get install --reinstall libgl1-mesa-dri

Then reboot and see if that restores your interface.  Please post back and let me know if it didn't work and you need more assistance.  If you want, after this is resolved, I will walk you through the proper process to enable you to use the latest Catalyst driver, if it supports your hardware.

---

