---
title: "Firewire Unstable"
date: 2011-01-11
forum: Hardware
---

### Post by bml137 on 2011-01-11
I am using mythbuntu 10.10 with xorg-edgers repo.  The main culprit here is the 2.6.37 kernel or the new firewire system.

This worked fine back in kernel 2.6.28 or whenever the firewire module was raw1394.  Now the modules are firewire_core and firewire_ohci.

I have a firewire cable plugged into a digital cable box.  I use it to change the channel.  The whole thing functions fine (at first).

Every second, I get the following line in my log:
```
firewire_ohci: isochronous cycle inconsistent
```

I also get the following line every so often:
```
irq_handler: ## callbacks suppressed
```
## is a number that ranges from 1 to several hundred

Eventually, 'plugreport' doesn't recognize the device anymore.  It seems to be when the callback count near 1000.  Sometimes this happens within minutes and other times it will take several hours.

My current solution is to not load the firewire modules and only load them when I call the channel changer:
```
/sbin/modprobe firewire_core
/sbin/modprobe firewire_ohci
sleep 1
/usr/bin/mythchanger -f 4 -P -c $1
rc=$?
sleep 2
/sbin/modprobe -r firewire_ohci
/sbin/modprobe -r firewire_core
exit $rc
```

I had to set the suid bit on modprobe so the 'mythtv' user can execute it (setting the suid bit on this script doesn't seem to work).

Is this a known problem?

---

### Post by bml137 on 2011-01-15
Ok, I have narrowed down the issue, but it is still unsolved.  However, this may help someone diagnose it.

When I am not watching TV or a recording, plugreport returns valid information about the device.  When I am watching a recording (HD or SD...not even live), plugreport comes back as if no devices are attached.

The HDMI port is in use all the time.  I am simply switching to something that is using X and CPU more intensively.  It never happens when I am streaming video/audio over the internet.

Thanks in advance.  I hope someone can figure this crazy issue out. :)

---

### Post by bml137 on 2011-01-15
After even further investigation, I have found that this doesn't have to do with ALSA dmix over HDMI.  I can play music over that device and still run 'plugreport' without issues.

I has to have something to do with video having a devastating effect on firewire.  Firewire becomes inoperable when I am playing video.

---

### Post by bml137 on 2011-01-16
I downgraded to the 2.6.35-12 kernel and started using the raw1394, ohci1394, and ieee1394 kernel modules for firewire.  This looked like it solved the problem.

Then I updated my V4L to get the HDPVR to work properly and the problem came back.  After further searching, I think I found the issue and I might just log it as a kernel bug.

To summarize:

2.6.35 w/o V4L update & not playing MythTV video: firewire works 100%
2.6.35 w/ V4L update & not playing MythTV video: firewire works 100%
2.6.35 w/o V4L update & playing MythTV video: firewire works 66%
2.6.35 w/ V4L update & playing MythTV video: firewire works 0%
2.6.37 not playing MythTV video: firewire works
2.6.37 playing MythTV video: firewire works 0%

I tried using both ffmpeg and libmpeg2 decoders.  I also tried using *1394.ko and firewire_*.ko modules.  All of these tests were with the radeon.ko DRM module.

---

### Post by bml137 on 2011-01-16
I downgraded to the 2.6.35-12 kernel and started using the raw1394, ohci1394, and ieee1394 kernel modules for firewire.  This looked like it solved the problem.

Then I updated my V4L to get the HDPVR to work properly and the problem came back.  After further searching, I think I found the issue and I might just log it as a kernel bug.

To summarize:

2.6.35 w/o V4L update & not playing MythTV video: firewire works 100%
2.6.35 w/ V4L update & not playing MythTV video: firewire works 100%
2.6.35 w/o V4L update & playing MythTV video: firewire works 66%
2.6.35 w/ V4L update & playing MythTV video: firewire works 0%
2.6.37 not playing MythTV video: firewire works
2.6.37 playing MythTV video: firewire works 0%

I tried using both ffmpeg and libmpeg2 decoders.  I also tried using *1394.ko and firewire_*.ko modules.  All of these tests were with the radeon.ko DRM module.

---

### Post by bml137 on 2011-01-16
Here is some 'dmesg' output related to when the firewire "loses it":
```
[35467.350038] firewire_core: BM lock failed, making local node (ffc0) root.
[35467.350044] firewire_core: phy config: card 2, new root=ffc0, gap_count=5
[35467.370270] firewire_core: skipped bus generations, destroying all nodes
[35467.560045] firewire_core: giving up on refresh of device fw1
[35467.870131] firewire_core: rediscovered device fw0
```
Here is the 'dmesg' output related to when the firewire gets back to normal:
```
[35471.021023] firewire_core: rediscovered device fw1
```

Kernel bug has been submitted...

---

### Post by bml137 on 2011-01-22
The heart of the issue was that the firewire card had actually gone bad.

---

