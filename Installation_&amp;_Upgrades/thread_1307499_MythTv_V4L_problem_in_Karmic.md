---
title: "MythTv V4L problem in Karmic"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by AntonL on 2009-10-31
Hi, since upgrading to Karmic I have a problem using my USB based TV Capture on Karmic Server edition.

I think I need to explain the time line a little bit.
Tomorrow all analogue tv signals here in Denmark are being shut down, in preparation of that, I decided two days ago to setup a mythtv backend on my server. (Unfortunately this co-incided with the release of 9.10)

1) I had a beta of 9.10 running on my desktop
2) Installed TVTime TVplayer on my desktop
3) Verified that my quaint capture device worked
4) Installed MythTV on my server (9.04)
5) Configured my capture device
6) Installed MythTV frontend on my desktop
7) The frontend complained that the version of my backed database was from a previous version, and that I should upgrade.
8) Upgraded my server to 9.10 (actually it is a complete re-install)
9) Installed MythTV backend on my new 9.10 server
10) Registration of my capture device fails, (Failed to open, Could not open '/dev/video0' to probe its input)

the odd thing is, my 9.10 desktop recognises the hardware, and I'm pretty certain that the 9.04 server accepted it as well, although I never did get arround to verify it, I'm pretty certain the 9.04 based MythTv accepted my hardware as well.

When examining the dmesg log from the server, and comparing it to the log from my desktop, I notice some differences, leading me to believe that there is a difference between the versions of em28xx.

I then tried to download the latest em28xx and compile that on my server, but the compilation process fails.

Any suggestions on how to move forward from here is greatly appreciated

---

### Post by AntonL on 2009-10-31
I managed to resolve one issue, the account running mythtv-setup was not a member of the group "video", when I fixed that, mythtv was able to detect the capture device, however, the backend crashes when trying to use the device.

Which is odd, since it works on the desktop. although I'm still mystified by why the em28xx logs different messages on the server compared to the desktop.

---

### Post by AntonL on 2009-11-01
I gave up, and installed Mythbuntu on my server, and everything seems to work now

---

### Post by budi_indira on 2009-11-11
I've a Gadmei UTV 330+ and face (I think, the same) problem like you..

I have read anywhere (on the milis), that Gadmei UTV 330 driver is already added into the kernel 2.6.31, the one that Karmic use. That's true, as Ubuntu 9.10 detect it automatically (Detected as Gadmei UTV 330 via **lsusb**).


Something odd is the tuner isn't registered as a video device when it plugged!! (like, /dev/video0)


How could I use it, if it doesn't registered as a video device????

Maybe somebody know, how to registered it into the system..

Thanks

---

### Post by budi_indira on 2009-11-11
**Sorry**
Double post.. >,<

---

