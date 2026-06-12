---
title: "Radeon HD7750, has anyone had any success using this graphics card?"
date: 2014-11-18
forum: Hardware
---

### Post by Handssolow on 2014-11-18
I bought a Radeon HD7750 a while back. On an existing install of Ubuntu 12.04 LTS 64 bit I got boot and error messages and made no progress. It would fire up a GUI using a live DVD though that wasn't using an AMD driver. Longer term success came using instead an HD7950 though it was more expensive.

With the HD7750 still on a shelf, this week I thought I'd have another on a 2 core AMD PC with Ubuntu 12.04 LTS 32bit. The rather ancient GeForce 6600GT needs to be retired. No luck, no difference, lots of error messages, Hda codecs out of range, too many HDMI devices, Gnome setting Manager not reponding, Hda- codecs cannot build controls for #0 (error -16), I gave up and put the 6600GT back in and the HD7750 back on the shelf.

The only idea I have left is to try using the HD7750 with a fresh install which I might try with a spare HD when I've got the time.

After many Web searches I don't hold out much hope, yet apparently AMD supports HD7xxx graphics card. Perhaps my HD7750 isn't one of them.

Has anyone had success using a Radeon HD7750 on a desktop running Ubuntu (or other Linux OS), stable system with high end driver?

---

### Post by Handssolow on 2014-11-22
I got my HD7750 card working though a new install. Fortunately I had enough bits around to make up another desktop.
It's an Asrock 939 Dual Sata mobo, 2 core 2400+ AMD, 2G DDR running 14.04 LTS 64bit with the HD7750 connected to the VGA input on a 15" LCD TV. 

From a 14.04 live DVD and wired ethernet, installation went with few hitches after I sorted out the deleting and re-partitioning of a previously used HD. The Addition Drivers seettings showed hardware drivers had been automatically installed and identified as-
Gallium 0.4 on AMD Cape Verde Pro

I wonder if I downloaded the latest Catalyst driver from AMD it might perhaps offer something slightly better but the current solution seems to work for now.

For those trying to get a HD7750 working on an existing system as I was last week, for what it's worth, I note this thread also mentions the hda-codec issue I was having.
 
[http://ubuntuforums.org/showthread.php?t=2125753&highlight=Radeon+7750](http://ubuntuforums.org/showthread.php?t=2125753&highlight=Radeon+7750)

---

