---
title: "Ubuntu 12.04 and Nvidia Graphics (NVS 280)"
date: 2014-03-10
forum: Hardware
---

### Post by **FuSeD** on 2014-03-10
I have a Dell Optiplex GX520 running Ubuntu. It was working perfectly until I installed a new graphics card. The Nvidia Quadro NVS 280. After I installed it in my pc It wouldn't boot up it just kept restarting. I think the driver I needed was Nvidia-96 but I'm not sure I couldn't get it to install anyway just kept saying I've held broken packages and no matter what I tried I couldn't fix it. I tried Synaptic to try get rid of the broken packages and nothing, I tried using -f command in terminal and nothing.

The live CD wouldn't boot either just kept making my pc restart. I could get it to boot if I went into the recovery mode and then just asked it to boot normally but I couldn't get it to realise that the graphics card is dual screen and it just displayed the desktop on both screens. I tried the card with an older version of Ubuntu 10.10 and it worked perfectly, booted up just fine, recognised the dual screen output but 10.10 is no longer supported :( How can I get the graphics card to work in 12.04? Any help at all would be a great help I've been sat here for days trying to figure this out and I'm all out of ideas. I read something about a feature in Ubuntu 11 that causes issues but I don't know if that applies here.

---

### Post by Yellow Pasque on 2014-03-10
Install Ubuntu 12.04.1 because it still has a 3.2.x kernel and Xserver 1.11.x: [http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)
That will allow you to use the nvidia-96 driver whereas newer versions of 12.04 won't.

---

### Post by **FuSeD** on 2014-03-10
No luck with 12.01 or 12.03 :( I just get a blank screen, can't get it to boot the live cd. It didn't keep restarting this time though just sat there.

---

### Post by Yellow Pasque on 2014-03-10
Try booting with nomodeset ?

---

### Post by **FuSeD** on 2014-03-10
Ok that worked thanks :) got it to boot up. Still have the same problem with the graphics though. I can get the card to work great in 10.10 from default. I don't get why I'm having so much trouble with newer releases. Honestly I think it would just be easier to try work with 10.10 but I can't use sudo apt-get as packages are no longer available.

---

### Post by Yellow Pasque on 2014-03-10
> Still have the same problem with the graphics though
Be more specific. Did you install the nvidia-96 driver?

---

### Post by **FuSeD** on 2014-03-10
No I got the same issue with the broken packages. Thanks for your help though. I think I'm just going to throw in the towel on this one and get a different graphics card.

---

### Post by beerninja on 2014-03-26
I have this exact same problem.  Optiplex GX520 with a PCI Nvidia NVS 280.  Infinite boot loop.  I can get in with nomodeset but the nouveau drivers seem to just crap out and cause boot loop or something.  I forced install of nvidia drivers 331.49 (which according to nvidia.com fully support the NVS280) but it gives me artifacts all over the screen.  I am going to try a couple of different distros to see if I can get one to work.  I already tried ubu 13.10, mint 16, mint debian, and even puppy linux and all cause boot loop except puppy which just says "boot error" and freezes.  I think tomorrow the final beta for 14.04 comes out so I guess I'll give that a shot.

I'm not sure if maybe there is a conflict with the built-in intel graphics which cannot be disabled unless a pci-e x1 card is inserted (according to the bios).  If it comes down to it i'll grab a pci-e x1 card off of ebay and see what happens.

---

### Post by beerninja on 2014-03-28
update:  here are the following distros I tried

Ubuntu 14.04 final beta live CD - boot loop.  Can get in with nomodeset.  Tried installing proprietary nvidia driver during live CD from the "Additional Drivers" menu which for some reason recommended nvidia-173 (version 173.14.39) even though nvidia.com recommends 331.49.  Anyway it didn't work.  It was stuck in software rendering mode regardless of what I did.

Mint 16 (based on 13.04 I think) cinnamon - boot loop.  Same as above.  Tried newest nouveau from xorg-edgers, and also tried nvidia-331 (331.49).  Corrupted screen and turned off second monitor as soon as I installed it.

Mint Debian - same as Mint 16

Puppylinux - won't even boot live CD.  Says "boot error" and freezes.

Mint 13 (based on 12.04) Cinnamon - Actually does not cause a boot loop but fails to load X and spits out the following in the error log: "Fatal Server Error: no screens found".  If I start in recovery mode, it boots but in the system info it says the graphics driver is in "fallback mode" (whatever that is) so all the windows are very laggy.  Fallback mode doesn't seem to be nearly as bad as software rendering mode though.  I tried to delete the xorg.conf file completely thinking that it would solve the no screens found problem but it did nothing.  I think the integrated intel graphics are causing the problem.

Mint 13 (based on 12.04) XFCE - boots and runs flawlessly.  I have to enable dual screen manually with xranr which is kind of a pain in the ass but hey it works.

I think next I'll try to find a way to blacklist the intel graphics...

---

### Post by 915086731 on 2014-09-29
I am also using nvs 280 now. You can try the default open source driver nouveau, the key issue is that you should use xfce desktop environment. The unity and gnome 3 will fail under the old graphic card.

---

