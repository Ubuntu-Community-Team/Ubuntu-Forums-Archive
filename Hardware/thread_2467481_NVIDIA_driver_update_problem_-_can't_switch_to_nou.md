---
title: "NVIDIA driver update problem - can't switch to nouveau"
date: 2021-09-28
forum: Hardware
---

### Post by calmdownmonkey2 on 2021-09-28
Hi,

My system works fine with the current version of the NVIDIA driver I have installed, which is nvidia-driver-470.

However, the software updater wants to install loads of updates to this driver, and if I let it, my PC becomes unbootable (can't see login screen - just a blank grey screen). I have to use Timeshift to revert to get it working again.

I could simply ignore NVIDIA updates, but it's a pain to have to uncheck all the NVIDIA related stuff every time I do an update, and I'm not sure how long I can keep doing that, so I thought I'd try to fix this.

I thought I'd try to change back to Nouveau drivers, then purge NVIDIA and start again with it, to see if I have better luck. However, if I try to select Nouveau in the "Additional Drivers" panel, I get this error (pic below). I tried basic troubleshooting steps I found online, like cleaning up packages, but it doesn't seem to make a difference.

I'm not experienced enough to know the next best thing to try (rather than make it worse), so I thought I'd ask for help. How can I get a nice clean start with NVIDIA?

I'm on Ubuntu 21.04. Thanks a lot!
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289209&stc=1[/IMG]

---

### Post by rsteinmetz70112 on 2021-09-29
I've done this before by purging all nividia packages. This may not be the cleanest way but it worked for me;

```
$ sudo apt purge *nvidia*
$ sudo reboot
```

You might wat to add --dry-run to the above command to see what it will remove.

---

### Post by calmdownmonkey2 on 2021-09-29
> **rsteinmetz70112 said:**
> I've done this before by purging all nividia packages. This may not be the cleanest way but it worked for me;

```
$ sudo apt purge *nvidia*
$ sudo reboot
```

You might wat to add --dry-run to the above command to see what it will remove.

Thank you, that did the trick. I purged, rebooted, then cleanly installed the NVIDIA 470 driver and everything seems to be okay now.

However, I had to uncheck the repository "http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/". If I leave this checked, it tries to pull down some NVIDIA updates which breaks my system again. Is it alright to leave it this way forever (i.e., with that repository unchecked)? Does it mean I'll never get driver updates at all now?

I have no idea why these particular updates from that repo break my system so badly.

I'm on this one at the moment: 
NVIDIA Driver Version:470.63.01
Server Version Number: 11.0
Server Vendor Version: 1.20.11 (12011000)
NV-CONTROL Version: 1.29

---

### Post by rsteinmetz70112 on 2021-09-29
Simply remove the ppa from your sources. It won't hurt anything. That ppa has drivers for various graphic chips. 
```
sudo add-apt-repository --remove ppa:launchpad.net/graphics-drivers/ppa/ubuntu/
```
I may not have the exact name of the ppa right, but you get the idea.
You also probably want to do an update after it's removed.

---

