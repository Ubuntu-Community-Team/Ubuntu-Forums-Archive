---
title: "Sound Problems in Ubuntu"
date: 2008-06-15
forum: Hardware
---

### Post by krishnadevsreekumar on 2008-06-15
Hi,
I'm a user who's new to Ubuntu, having just migrated from WinXP. Everything is working absolutely superbly with Ubuntu except the sound. During the first or second boot of Ubuntu, the sound worked perfectly fine. But now, it aint working at all. I have a Creative SoundBlaster Live 5.1 sound card.Could anyone help me out here? Please. Again, I'm not able to mount my external hard drive either. The icon shows up in the Computer window but I recieve an error message upon trying to mount. The External HDD is NTFS but I believe that has no relevance in Ubuntu 8.04 right? Please help me out here...

---

### Post by Pjotr123 on 2008-06-15
Sound: check this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

External disk: boot Windows and "safely remove" (unmount) the disk in Windows. Windows then writes a stop code that Ubuntu needs. That should do the trick.  :-)

---

### Post by krishnadevsreekumar on 2008-06-15
Hi.. Thanks for the advice. I did as you advised. I disabled my onboard from the BIOS settings. But still, I aint getting sound. I mean, I do not get any system sound or application sound or anything but upon changing the volume settings, I get these deep beat kind of sounds from my speaker. Like, it responds to the changes in volume setting but somehow there ain't any sound. Please tell me what can I do to solve this??

---

### Post by Aruhn on 2008-06-15
Probably it works with PulseAudio.

I had similar problems with my Creative Soundblaster 5.1 (external Soundcard) and the only help was PulseAudio.

This did I do:
1. I installed libasound2-plugins and pavucontrol
2. I opened pavucontrol and choose my external soundcard as default Hardware
3. I opened /etc/pulse/daemon.conf and configured 6 channels (default-sample-channels = 6).
5. Last, I choose by all Audio featues (System --> Audio) PulseAudio - Soundserver
4. Restart

Since then, my external soundcard works fine. :)

---

### Post by krishnadevsreekumar on 2008-06-20
Thanks Aruhn. The problem has been solved. Thanks a million! :)

---

### Post by johntelthorst on 2008-06-20
I just installed Ubuntu, and the sound isn't working for me either.  I went to [http://ubuntutip.googlepages.com/sound]("http://ubuntutip.googlepages.com/sound").  I have an acer TravelMate 2440, so I tried to follow the instructions for 6.  They worked fine, until I ran the command:

```
sudo apt-get install linux-backports-modules
```

For which I get the following error:

```

E: Couldn't find package linux-backports-modules
```

Any assistance would be helpful.

---

### Post by Pjotr123 on 2008-06-20
> **johntelthorst said:**
> I just installed Ubuntu, and the sound isn't working for me either.  I went to [http://ubuntutip.googlepages.com/sound]("http://ubuntutip.googlepages.com/sound").  I have an acer TravelMate 2440, so I tried to follow the instructions for 6.  They worked fine, until I ran the command:

```
sudo apt-get install linux-backports-modules
```

For which I get the following error:

```

E: Couldn't find package linux-backports-modules
```

Any assistance would be helpful.

Weird. Have you enabled all software sources (repositories)? If not, enable them as a byproduct of applying this how-to:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Afterwards, try to apt-get it again.

---

### Post by Nepherte on 2008-06-20
You need to install linux-backports-modules-hardy (assuming you're running hardy heron):
```
sudo apt-get install linux-backports-modules-hardy
```

---

