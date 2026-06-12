---
title: "Hard Drive Problem?"
date: 2010-10-16
forum: Hardware
---

### Post by ubunwhat? on 2010-10-16
Hi,

Two days ago I started experiencing problems with my laptop. I have both Windows 7 and Ubuntu 9.10 in dual boot.

Booting Ubuntu became extremely slow. It take around 2 minutes while before it would take 10 or 15 seconds after the grub menu.

When I try to boot Windows, it stay on the loading screen, with the Windows logo, for about 2-3 minutes before the computer reboot by itself. When trying to open Windows in safe mode, it freeze on the following line every time:
"Loaded: \Windows\system32\DRIVERS\CLASSPP.SYS
 Please wait..."
for 2-3 minutes and then reboot by itself. In other words, I can't open Windows at all.

In addition, I occasionally hear clicking and beeping noises that come from the hardware. I never heard them before.

All those symptoms appeared suddenly: everything was fine in the afternoon and next time I tried to use my laptop I had all those problems.

From what I red, the clicking noises seems to point toward a hard drive issue. I tried to run a "HDD diagnostic program" that I found in the BIOS menu and I aborted it after 45 minutes since it didn't move from 0%. 

Those anyone have suggesting of what I should do?

---

### Post by spikoley on 2010-10-16
It sounds like there might be something wrong with your hard drive.  Boot into the live CD and try repairing it with the following command.

```
sudo fsck /dev/sda1
```

The sda1 might be something else.  If you do not know the name of your drive then run *gparted*.  It should list the name of the drive.  Just replace the sda1 with the name of your drive.

I am not sure if this will work, but its a worth a shot.

---

### Post by coffeecat on 2010-10-16
> **ubunwhat? said:**
> Those anyone have suggesting of what I should do?

You'll need to download the ISO for either 10.04 or 10.10 because I'm going to suggest you use Disk Utility and I seem to remember that Disk Utility in 9.10 gave false positives.

First - I suggest you use that machine as little as possible in case you have data you need to rescue. If the clicking does mean a failing drive, it could fail suddenly and quite soon.

Do you have another machine to download and burn an ISO to CD? If so, here's your download link:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I suggest you get 10.10 rather than 10.04 because I'm fairly sure the version of Disk Utility is a later one. Boot up from the live CD and go to System > Administration > Disk Utility. Click on the hard drive entry in the left pane and then look for "Smart Data" - "View SMART data" in the right pane. Not all drives support SMART, but that might give you some useful information if yours does. You can run a self-test but that might be the last straw if the drive is really failing.

---

