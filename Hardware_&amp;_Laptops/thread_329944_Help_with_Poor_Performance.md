---
title: "Help with Poor Performance"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by scaryant on 2007-01-02
Hi There,

Recently I did my annual conversion from Windows to Linux, particularly because XP seemed to be getting slower and slower as time went on. This time on advice from others I decided to try Ubuntu.

I like it a lot so far, however performance is pretty poor using KDE/Gnome maybe even a little worse than XP was!? Having used other distros redhat and madrake on the same machine a year or two ago I was expecting better performance to be honest. Is this simply because my specs (below) aren't good enough for Ubuntu (given the GUI seems to be a little "nicer") or do I need to do some tweaking? I managed to find the services and disable a couple (eg Bluetooth which I don't have) but there wasn't much else to disable from what I saw.

Anyway, here's my specs:

Toshiba Satellite Pro 4600 (Laptop)
CPU: PIII 900Mhz
RAM: 384 Mb (172Mb used, running only KDE & sysmon)
HDD: 20 Gb
VID: 16 Mb Video Card
SWAP: 807 Mb (80 Kb used)

Many thanks for comments or advice.

---

### Post by aysiu on 2007-01-02
Your specs are a bit modest, to be honest. I think you should try *kde-core*, XFCE (aka Xubuntu), or something even lighter like IceWM or Fluxbox.

[http://www.psychocats.net/ubuntu/kde-core](http://www.psychocats.net/ubuntu/kde-core)
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by ferebee on 2007-01-02
My Computer is a PIII 600mhz, 384mb ram, with Ubuntu installed on  a 10gb partition, and it runs well with Gnome, and much better with XFCE. When I swapped out my old 32mb ATI video card with a much newer 128mb Nvidia card  performance was much improved. Perhaps the video card is affecting performance?

---

### Post by zgornel on 2007-01-03
> **scaryant said:**
> Hi There,

Recently I did my annual conversion from Windows to Linux, particularly because XP seemed to be getting slower and slower as time went on. This time on advice from others I decided to try Ubuntu.

I like it a lot so far, however performance is pretty poor using KDE/Gnome maybe even a little worse than XP was!? Having used other distros redhat and madrake on the same machine a year or two ago I was expecting better performance to be honest. Is this simply because my specs (below) aren't good enough for Ubuntu (given the GUI seems to be a little "nicer") or do I need to do some tweaking? I managed to find the services and disable a couple (eg Bluetooth which I don't have) but there wasn't much else to disable from what I saw.

Anyway, here's my specs:

Toshiba Satellite Pro 4600 (Laptop)
CPU: PIII 900Mhz
RAM: 384 Mb (172Mb used, running only KDE & sysmon)
HDD: 20 Gb
VID: 16 Mb Video Card
SWAP: 807 Mb (80 Kb used)

Many thanks for comments or advice.

Put as much ram in as possible (1gb would be great but 512 does the job too)

---

### Post by scaryant on 2007-01-06
Thanks for the tips, I've installed Xubuntu and it doesn't really seem to improve performance that much. Hm. No matter...

I did also find this [article]("http://www.tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed") on tweak speed for Ubuntu. Seems to have made a difference most notably now RAM seems to be running at 87 Mb which is much better... hard to tell if this was directly related to these tweaks though. Anyway that should help a little.

Thanks again

---

### Post by RandomJoe on 2007-01-06
Do you know if your CD and hard drive are on the same controller port?  My Dell Latitude C840 had hideous performance, and I found that the HAL was polling the CD drive every few seconds (in case I stuck a CD in, so it could automount) which apparently "blocks" the I/O channel the drive is on every time it does that.  The CD on this model shares the primary channel with the hard drive so all HD access also gets ground to a halt, thus making the system run like molasses any time it has to access the hard drive.

This thread discusses the issue:
[http://www.ubuntuforums.org/showthread.php?t=188901](http://www.ubuntuforums.org/showthread.php?t=188901)

I used the patch at the end of that thread to stop hald from polling my drive (happened to be that exact model) and the speed went back up, at the expense of course of not having auto-mount and such for the drive.

---

