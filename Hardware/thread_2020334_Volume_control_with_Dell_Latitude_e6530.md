---
title: "Volume control with Dell Latitude e6530"
date: 2012-07-08
forum: Hardware
---

### Post by Calimo on 2012-07-08
Hello,

I installed Ubuntu 12.04 on a Dell Latitude e6530. Apparently everything works fine except one thing: volume control (sound itself is fine).

I have 3 hardware buttons (mute, - and +) that are inactive. In addition I cannot move the volume slider that appears in Unity's indicator zone: it is blocked at minimum volume. Same if I open the sound parameters: the sliders at the bottom are blocked. In addition the "Test sound" button doesn't play any sound, and in the Applications tab nothing is displayed, even if Rhythmbox is currently playing.

This isn't a sound problem: audio files play normally in Rhythmobx (I can hear the sound playing perfeclty normally with good quality), and I can even tune the volume in applications (ie Rhythmbox slider).

Weird thing is: the volume control slider is active on the login screen (not the hardware buttons). Weird thing 2: both slider and hardware buttons work in KDE.

I searched a bit on the topic, but I couldn't find anything similar. Apparently I have an Intel QM77 chipset with integrated Intel HDA 4. This chipset is [certified](http://www.ubuntu.com/certification/catalog/component/pci:8086:1E55/) (even though not on that specific model), so I don't understand why it is a problem.

Do you have any idea what happens and how I could solve this issue?

Thanks a lot,
Calimo

---

### Post by cipherboy_loc on 2012-07-08
Try running this command in the terminal, and checking whether you get output when pressing the buttons.
```

xev

```

Also, have you played around in gnome-control-center?


Cipherboy

---

### Post by Calimo on 2012-07-08
Thanks cipherboy_loc!

xev gives me a lot of 

```
MotionNotify event, serial 36, synthetic NO, window 0x4200001,
    root 0xb7, subw 0x0, time 477384, (119,170), root:(185,222),
    state 0x10, is_hint 0, same_screen YES
```Sounds about right.

I did play in Gnome control center but all sound options are disabled. :confused:

---

### Post by Calimo on 2012-07-08
Well, I finally figured out it was a permission problem. I found a lot of the following lines highlighted in red in /var/log/syslog:

```
Jul  8 14:38:56 marvin pulseaudio[21246]: [pulseaudio] main.c: Failed to acquire autospawn lock
Jul  8 14:38:59 marvin pulseaudio[21248]: [autospawn] core-util.c: Failed to create secure directory: Permission denied
```

It was a problem with the permissions on my home dir. I had it mounted on a NTFS directory, and apparently that's bad, pulse need different permissions that can't be set on NTFS.

So I moved my home dir to the root file system (ext4) and... yes, it works! Even the hardware buttons.

I'm going to move my dual-boot shared files back to my big partition now.

I knew it was a stupid thing, but that's one of the most stupid things I've ever encounterd:lolflag:
Anyway, it's working now. Thanks a lot for your help and your time!!! :D

---

