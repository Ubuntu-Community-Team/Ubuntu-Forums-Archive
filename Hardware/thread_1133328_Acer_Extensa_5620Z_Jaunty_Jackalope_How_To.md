---
title: "Acer Extensa 5620Z Jaunty Jackalope How To"
date: 2009-04-22
forum: Hardware
---

### Post by chrisby on 2009-04-22
Hardy required some hacking to initially get everything to work.  Jaunty doesn't require any hacking, but has random freezes due to a intel graphics bug.  Here is a report of my findings with the Jackalope through RC: 

Things that work out of the box with no resume issues:
1. Suspend/Hibernate
2. Built in microphone
3. All audio ports (line in, microphone jack, and headphone jack)


The line in and microphone jack are muted by default.  To unmute use alsamixer from the terminal and adjust

If the built in speakers are too low, or you need to use alsamixer to increase the volume. 

4. Ethernet
5. SD Card Reader (tested with SD card only)
6. Broadcom Wireless (Those with Atheros Wireless please post if it works)

Things that currently don't work:
1. Compiz and all desktop effects
because of a critical bug that results in system freezes, Intel 965 cards have been blacklisted.  You can re-enable at your own risk (I haven't had good luck with this).  

See [http://ubuntuforums.org/showthread.php?t=1129055&highlight=compiz]("http://ubuntuforums.org/showthread.php?t=1129055&highlight=compiz")

or the ongoing bug report: 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392")

If I missed anything, please post.

---

