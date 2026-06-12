---
title: "Matsushita DVD drive fails to read some discs"
date: 2010-05-21
forum: Hardware
---

### Post by Peter Bell on 2010-05-21
I find this problem a little puzzling!

My Shuttle X200 (running Lucid) came with a Matsushita UJ-85JS DVD/CD (PATA laptop slim) drive installed.

I find that it totally refuses to recognise some DVDs (eg the Video Wimbledon) - all attempts to access /dev/sr0 report that there is no disc loaded.  Other DVDs will load and play without problem.

I also have a Samsung SH-S222 drive in a USB enclosure.  When I connect this drive to the Shuttle it will load and play the Wimbledon disc without any problem.

I removed the UJ-85JS drive and installed it in my wife's laptop running Win XP.  XP quite happily loads and plays the Wimbledon disc in the Matsushita drive.

Both of the drives are running RPC1 firmware.

It doesn't appear to be a problem with the UJ-85 drive since it works perfectly under Win XP.

It doesn't appear to be a problem with the disc or encryption - that works perfectly in the Samsung drive under Ubuntu.

I haven't, knowingly, installed any special drivers on either machine for either of the drives.

Can anyone suggest what is going on here and, better still, how to fix it.

I use the Shuttle as a media server and not being able to read DVDs is a major drawback.

Apart from the standard AUDIO_TS and VIDEO_TS folders, the Wimbledon disc also contains some Windows s/w (visible both on the XP machine and under Ubuntu on the Samsung drive).

---

### Post by Peter Bell on 2010-05-24
Bump!

Has anyone any thoughts or suggestions on this?

---

### Post by dino99 on 2010-05-24
sudo update-pciids && update-usbids

you need the medibuntu repo:

[http://ubuntuforums.org/showthread.php?t=1491927](http://ubuntuforums.org/showthread.php?t=1491927)

sudo apt-get update
sudo apt-get install -f

---

### Post by Peter Bell on 2010-06-05
Wow!  That worked a treat - at least the Wimbledon DVD loads now.  Thank you very much!  I'll have to see how much of the rest of my collection is now readable.

Is there a simple explanation for what was wrong and what the update-pciids command actually does.  I'm still confused as to why some discs would work in the internal drive and others wouldn't, while all the discs I tried worked in the external drive.

I'm guessing that the ids file tells the drivers something about the capabilities of the hardware devices, but there must still be some significant difference between the various discs I tried.

Once again - thanks!

---

