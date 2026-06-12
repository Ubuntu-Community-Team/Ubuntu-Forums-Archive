---
title: "[SOLVED] Help, my microphone isn't working on Intrepid!"
date: 2008-12-25
forum: Hardware
---

### Post by Virtualboxbuntu on 2008-12-25
It wasn't working in Hardy, either. But it was working in Windows Vista.

Anyway, here's my problem:

My microphone is extremely quiet. If I put my mouth right next to it, you can faintly hear a muffled sound in Sound Recorder, Audacity, or any other program like that. According to Volume Control, my device is HDA NVidia (Alsa mixer).

I've tried setting all the recording devices to max volume and enabling audio recording, but whenever I close Volume Control, they reset themselves to disabling audio recording. Everything gets reset when I close it, whether I do it through the text-based alsamixer or Volume Control.

Please help me! If it helps, here's some info about my computer:

HP A1730N
1 mic jack and 1 line-in jack each on the front and back - all have the above problem
Linux Mint 6 (based on Ubuntu Intrepid)
NVidia graphics card + NVidia driver

The microphone has never worked in any Linux distro yet, but has always worked in Windows (which I don't want to ever see again).

---

### Post by gettinoriginal on 2008-12-25
Go to your Volume Control, switches tab and make sure mic and mic boost are checked  :)

---

### Post by Virtualboxbuntu on 2008-12-25
> **gettinoriginal said:**
> Go to your Volume Control, switches tab and make sure mic and mic boost are checked  :)

Thanks. They're actually under Playback, but it seems to have solved the problem.

Now for the next problem: my speakers are always playing whatever the microphone picks up. I mean that whenever the microphone hears something, the speakers play it. How do I stop this?

---

### Post by gettinoriginal on 2008-12-25
With mine, it was a matter of fine tuning the volume of the microphone.  I know sometimes if I am on chat with mic and headphones, the mic pics up the TV in the background.  Remember, the higher the volume on the microphone the more sensitive it is to background noise.

---

### Post by Virtualboxbuntu on 2009-01-01
I figured out the other problem too. Thanks a lot!

Wow, this kicks ***! I can control my new MacBook with my Wii Remote. At least I can with the LiveCD. The darn thing won't boot into Ubuntu. I posted a thread about it but I can't find it now.

---

