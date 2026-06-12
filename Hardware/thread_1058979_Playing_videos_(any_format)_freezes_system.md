---
title: "Playing videos (any format) freezes system"
date: 2009-02-03
forum: Hardware
---

### Post by smaw0351 on 2009-02-03
Dell Latitude E6400
Graphics - Intel GMA 4500MHD
Ubuntu 8.04

I just recently installed Ubuntu 8.04 on this new laptop.

Whenever I play any format videos in either Totem or VLC, the machine freezes / crashes and I have to hard reset it.

I do not have any problems watching videos in Firefox though.

Please help! It'd be nice to watch (legally) downloaded videos. ;)

---

### Post by smaw0351 on 2009-02-04
ok. the only way around it was upgrading to Intrepid. Now it seems i'm in the same boat as everybody else with Intrepid and the Intel GMA 4500MHD. Poor / slow performance. Compiz works but is slow when rotating the cube etc. It'll work for now until a better driver comes out for this chipset.

oh lawd!

---

### Post by danhiit on 2009-02-13
I have the same problem with my new compaq cq40. It hangs if i use mplayer or any other media player i am sure it the issue of graphic driver but couldn't figure out how and where to get 4500mhd driver. :(

I am searching for it and as soon as i found it i will update this thread for others.

bye for now.

---

### Post by danhiit on 2009-02-14
Hi friends

I have added line Driver "vesa" in device section of /etc/X11/xorg.conf and successfully ran media files.

Section "Device"
	Identifier	"Configured Video Device"
	[COLOR="DarkGreen"]Driver		"vesa"[/COLOR]
EndSection

Can you please check it in your systems and revert back with your findings?

---

### Post by densou on 2009-02-14
> **danhiit said:**
> bye for now.

[https://launchpad.net/~intel-gfx-testing/+archive/ppa](https://launchpad.net/~intel-gfx-testing/+archive/ppa)

it explains why newer driver requires Intrepid to work smoothly.

G4* cards support is *nearly preliminary* (X3*00 series is still affected by many bugs)

if you desire an update to LATEST release - not very stable -, you must upgrade nearly all system components (kernel+X server+MESA+driver+dependancies)
Work-In-Progress Jaunty has them all, but X server is still stuck to 1.5.99 and it could be broken at ease (note: Intel suggest that its package needs X server 1.6.0 not released yet, it's the next stable release)

Read this:
[http://intellinuxgraphics.org/results/2009-01-15__0/result.htm](http://intellinuxgraphics.org/results/2009-01-15__0/result.htm)

---

