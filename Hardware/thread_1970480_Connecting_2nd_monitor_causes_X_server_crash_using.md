---
title: "Connecting 2nd monitor causes X server crash using Nvidia drivers in 12.04"
date: 2012-05-01
forum: Hardware
---

### Post by zaziork on 2012-05-01
I have a secondary monitor connected to my Acer Aspire 8930 laptop. Graphics card is Nvidia GeForce 9600M GT (1GB).

My setup worked fine in all previous incarnations of Ubuntu; I installed the recommended Nvidia driver via "Additional drivers" and was able to connect and use the Samsung monitor through HDMI output.

The upgrade to 12.04 (64 bit) has rendered this impossible. As soon as I switch on the secondary monitor, the X server (and sometimes the entire system) crashes.

The problem is identical in both Unity (3D and 2D) AND Gnome (gdm).

It is, I believe, something to do with the Nvidia drivers, as connecting the monitor without the Nvidia drivers installed does not cause the crash. In this case, cloning the screen does work fine. This would suggest the problem does lie with the Nvidia drivers, and not for example the HDMI port or anything like that. However, this isn't a feasible solution, as I require the Nvidia drivers to be installed (video is chopped like carrots in a casserole when played without the Nvidia drivers, and playing HD content is out of the question).

I have tried both the Nvidia drivers available under "Additional Drivers"; the problem is identical with both. 

I have also clean installed 12.04 on my system twice, to ensure issue is replicated after an absolutely fresh install.

Like I said, everything was fine in 11.10. The issue appears to be the result of some change between 11.10 and 12.04, but I'm nowhere near able enough to begin to identify what is causing it.

Basic system specs: Acer Aspire 8930G: Intel Core2 Q9000, 4GB DDR3, GeForce 9600M GT (1GB), 250GB Seagate HD.

Any help or advice would be appreciated.

---

### Post by zaziork on 2012-05-02
Bump. Any ideas anyone?

---

### Post by zaziork on 2012-05-02
.

---

### Post by zaziork on 2012-05-05
In case anyone else has encountered this problem, I have tracked down where things are going awry. It is certainly an Nvidia driver issue, replicated over numerous installs of Ubuntu and Linux Mint.

In a nutshell, the latest Nvidia drivers cause immediate and repeated crashes of the xserver as soon as the external monitor is connected (via hdmi). The crashes of the xserver occur every 15 seconds or so, as soon as the login screen is presented after the first crash. The only way to resume X session is to disconnect or switch off the external monitor.

The problem was solved by reverting to older Nvidia driver. This is how this achieved on Linux Mint:

1. Open Synaptic and search for the package nvidia-current-updates.
2. Click on the package, then CTRL + E and select Force version to 280.13-Oubuntu5.1 (oneiric-security)
3. Click on "Force Version"
4. Select "Package" from the panel, and check the "Lock version" option in the menu.
5. Reboot.

The "Lock version" option means that the Nvidia drivers will not automatically update when newer versions are appear in the Repos. On one hand, future updates to the Xorg might not be compatible with the older Nvidia driver now installed on the system, which could lead to problems down the line. On the other hand, locking the version prevents the working Nvidia driver being replaced by a newer version that still may exhibit the issues outlined above. Then again, future updates of the Nvidia may (and hopefully will) fix these issues, so be sure to check every now and again to determine whether the newest version is cured of the problems. I opted to lock the current version for the time being to maintain stability of my system for as long as possible, but it's really anyone's guess what will happen first: Breakage due to incompatibility of the old Nvidia drivers with a future Xorg update; breakage being reintroduced due to replacement of the older Nvidia driver with even newer version (hence my locking of the version for now); or the problem being fixed in a new Nvidia driver release.

Hope this helps someone if they're going through the same external screen / xorg / Nvidia driver hell as I have.

---

