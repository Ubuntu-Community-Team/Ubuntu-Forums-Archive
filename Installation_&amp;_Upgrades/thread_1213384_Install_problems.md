---
title: "Install problems"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by ElJefeRocks on 2009-07-14
So, I had a working ubuntu, but in my last round of messing around and trying to have a working dev-build for my hardware (it needs as much help as it can get) i deleted my working distro.

Now I have been trying to get ANY ubuntu to install onto the machine.  I've tried 8.10 alternate cd, 9.04 desktop and alternates (cds and usb drives) and can't get karmic to boot either.  I can't even get a live CD up and running, so its really frustrating because I have nothing to work from or attempt a fix.

The only thing I get is the line:

```
udevd-event[3971]: inotify_add_watch(3, /dev/mapper/nvidia_gfefefaf, 10) failed: No such file or directory
```
and in console 1,
```
Loading, No block devices found
device-mapper: table: 252:0: raid45: unknown target type
device-mapper: table: 252:0: raid45: unknown target type
device-mapper: table: 252:0: raid45: unknown target type
...
device-mapper: table: 252:0: raid45: unknown target type
```

until it just gives me a blinking cursor after about 2 minutes.  I've waited a LONG time (overnight) for it to do something, and it didn't move.

System specs: Boot drive: 5400 rpm sata-120gb, first raid: 3x1.5tb sata, second raid 4x250gb sata, AMD 790GX SB750, AMD 7750, and 2gb ram with a nvidia 7950GX2 for graphics.

I haven't been able to get any dmesg or log outputs because it just stops and I have to reboot.  If anybody knows a way to get past this problem, please let me know, its driving me nuts.

---

### Post by jerrrys on 2009-07-14
[http://www.google.com/search?q=udevd-event](http://www.google.com/search?q=udevd-event)[3971&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a

thats all i could find, and no good...

maybe you should back up. have you burned all cd's using same drive and method?  live cd will not recognize RAID...

---

### Post by ElJefeRocks on 2009-07-15
I solved it by unplugging all of my drives and installing the desktop 9.04 distribution.  Then I worked my way up and installed mdadm from there and rebuilt the raids.  Now there are no problems (except the softreset failed - but it still boots).  Don't know what made it work but I can use the live-cds/usb now.

I have a feeling that it had something to do with a messed up drive that was part of the raid.  When I started it up my superblocks were a mess, but after I fixed that everything seems to be running fine.

Even though, shouldn't a live cd not mess with any of the hard drives in the system?  This is what makes me unsure of whether the drives were to blame or not.

---

